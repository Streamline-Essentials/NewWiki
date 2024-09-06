# Introduction to Streamline
**StreamlineCore** is a Minecraft plugin that adds endless functionality to Minecraft servers through what is known as **Modules**. These **Modules** are downloadable content that you insert into the `modules` folder within the StreamlineCore plugin to enhance your server.

Streamline Modules can provide a variety of features, and server admins and developers can even create their own using the plugin's intuitive API.

# Supported Server Types
Here are the server types that are natively supported by the plugin.

### Bukkit Version
> - Bukkit
> - Spigot
> - Paper
> - Purpur
> - ImmanitySpigot
> - Forks of the above that don't modify core code.

### Bungee Version
> - BungeeCord
> - Waterfall
> - Travertine
> - Flamecord
> - XCord
> - Other BungeeCord or Waterfall forks that don't alter core code.

### Velocity Version
> - Velocity
> - Velocity forks that don't modify core code.

# Streamline Requirements
There are requirements for **Velocity** and **Bungee**, while **Bukkit** requires two plugins.

### Bungee and Velocity Requirements
> - **LuckPerms**
>    - Found here: [click this text](https://luckperms.net/download)

### Bukkit Version Requirements
> - **LuckPerms**
>    - Found here: [click this text](https://luckperms.net/download)
> - **BukkitOfUtils**
>    - Found here: [click this text](https://www.spigotmc.org/resources/118276/)

# Installation
*To install Streamline, follow these steps:*

1. **Check** the list of requirements and download/install the necessary plugins.
2. **Download** the plugin from [here](https://www.spigotmc.org/resources/83659/).
3. **Insert** the plugin into your server's `plugins` folder.
4. **Start** and then **stop** your server.
5. **Add Modules**. Read [here](#useful-links) for more about modules.
6. **Configure** the plugin. Read [here](#configuration) for configuration instructions.
7. **Start** your server.
8. **Enjoy**! Leave a rating [here](https://www.spigotmc.org/resources/83659/) if you find the plugin useful.

# Configuration
Streamline offers many features for your server, so the configuration may seem extensive. This section aims to guide you through it.

### File System Layout
The main folder:
![Main Folder Explanation](main-folder-explanation.png)

The `commands` folder:
![Commands Folder Explanations](commands-folder-explanations.png)
# Developer API
Streamline was developed with developers in mind, featuring a robust API that is professionally managed.

## Import StreamlineCore
### Maven
**Repository**
```XML
<repositories>
	<repository>
		<id>jitpack</id>
		<url>https://jitpack.io/</url>
	</repository>
</repositories>
```

**Dependencies**
```XML
<dependencies>
	<!--Main API-->
	<dependency>
		<groupId>com.github.Streamline-Essentials.StreamlineCore</groupId>
		<artifactId>API</artifactId>
		<version>master-SNAPSHOT</version>
		<scope>provided</scope>
	</dependency>
	<!--Backend API (Bukkit, Fabric, Forge)-->
	<dependency>
		<groupId>com.github.Streamline-Essentials.StreamlineCore</groupId>
		<artifactId>API</artifactId>
		<version>master-SNAPSHOT</version>
		<scope>provided</scope>
	</dependency>
</dependencies>
```

### Gradle
```Groovy
repositories {
    maven { uri("https://jitpack.io") }
}
```

**Dependencies**
```Groovy
dependencies {
    compileOnly("com.github.Streamline-Essentials.StreamlineCore:API:master-SNAPSHOT") // Main API
    compileOnly("com.github.Streamline-Essentials.StreamlineCore:BAPI:master-SNAPSHOT") // Backend API
}
```

## Useful Links
> - **SpigotMC Page:** [click here](https://www.spigotmc.org/resources/83659/)
> - **Modrinth Page:** [click here](https://modrinth.com/plugin/streamline/versions)
> - **Modules:** [click here](modules.md)