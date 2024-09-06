# BukkitOfUtils
*Welcome to the main wiki page of **BukkitOfUtils**!*

We will be calling BukkitOfUtils "**BOU**" from here on out to simplify things.

## What is it?
BOU is a Bukkit plugin and API designed to ease the development process of making Bukkit plugins **that also include support for Folia**.

## How does it work?
When downloading a plugin that uses BOU, you also need to install the BOU plugin itself. This can be found here: [https://www.spigotmc.org/resources/118276/](https://www.spigotmc.org/resources/118276/)

It works by adding all of the necessary code for each plugin to work as a centralized plugin.

## Natively Supported

Below are the platforms and versions that BOU supports so far.

### Bukkit Platforms

> - Bukkit
> - Spigot
> - Paper
> - Purpur
> - Folia
> - Forks of the above (most supported):
>   - ImmanitySpigot
>   - FlamePaper
>   - AxolotlSpigot

### Minecraft Versions

> - 1.7 to 1.21+

# For Developers

*The plugin also comes with a nice API for developers to use.*

## Example Plugin

There is an example plugin found here: [https://github.com/ProjectsForAll/ExampleProject](https://github.com/ProjectsForAll/ExampleProject)

## API

Grab the API for your project with this:

### Add Repositories

#### Gradle Repo
```Kotlin
repositories {
    mavenCentral()
    maven {
        url = uri("https://jitpack.io")
    }
}
```

#### Maven Repo
```XML
to be added later
```

### Add Dependencies
#### Gradle Dep
```Kotlin
dependencies {
    compileOnly("com.github.Streamline-Essentials:BukkitOfUtils:master-SNAPSHOT")
}
```

#### Maven Dep
```XML
to be added later
```

### API Usage
The following will help you understand the API.

#### Correct Scheduling (Folia AND Bukkit Support)
**Notice:** *In order to support Folia, we have added a special Universal Scheduler to the plugin.*

**Entities and the EntityUtils class**
```Java
// Pass a boolean value in to indicate if you have called this method on the main Bukkit / Folia thread.
public static void damageAllEntities(boolean isCurrentlySync, double amount) {
    if (isCurrentlySync) {
        // Task is already in sync, so we go ahead and run it.
        damageAllEntitiesInSync(amount);
    } else {
        // Ensure that the task is being run in sync as Bukkit and Folia do not support async entity collecting.
        TaskManager.runTask(() -> {
            damageAllEntitiesInSync(amount);
        });
    }
}

// Only call this method if you are running it on the main thread (hence, "InSync").
public static void damageAllEntitiesInSync(double amount) {
    EntityUtils.collectEntitiesThenDo(entity -> {
        damageEntityInSync(entity, amount);
    });
}

// Only call this method if you are running it on the main thread (hence, "InSync").
public static void damageEntityInSync(Entity entity, double amount) {
    // Have to do this to support Folia.
    TaskManager.runTask(entity, () -> {
        entity.damage(amount);
    });
}
```

#### Async Task Timers (Repeating and Delayed Timers)
The API supplies a nice Task Timer class.

**NOTICE:** *These Task Timers automatically run asynchronously. So, when you are calling something that needs to be run synchronously, such as anything entity, location, or world-related, you must use the TaskManager class to make them run synchronously (on the Bukkit / Folia main thread).*

**Basic Repeating Timer**
This is a basic repeating timer.
```Java
public class BasicRepeatingTimer extends BaseRunnable {
    public BasicRepeatingTimer() {
        super(0, 20); // Waits 0 ticks (0 seconds) to run the first time, then runs once every 20 ticks (1 second).
    }

    @Override
    public void run() {
        // Do something here.
        
        // For example...
        DamageHandler.damageAllEntities(false, 1d); // As per our example above. "false" due to it being async (not in sync).
    }
}
```

#### Simple Configurations
The following is a simple example configuration using BOU's built-in ``SimpleConfiguration`` class.
```Java
public class ExampleConfig extends SimpleConfiguration {
    public ExampleConfig(BetterPlugin bouPlugin) {
        super(
            "config.yml", // The name of the file you want to be a configuration. (Will be created automatically.)
            bouPlugin, // Pass the BetterPlugin to it so it knows where to create the file. (You could also pass a File for a folder.)
            false // If the "config.yml" file is embedded into the plugin.
        );
    }
    
    @Override
    public void init() {
    }
    
    public String getMyLovelyString() {
        reloadConfig(); // Reload the config before getting the value.
    
        return getOrSetDefault("my.lovely.string", "BOU is really great!"); // Gets the string at my.lovely.string, or sets it as "BOU is really great!" then returns "BOU is really great!".
    }
}
```