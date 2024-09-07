# Pacifism
*This wiki page provides information about the plugin Pacifism.*

## Dependencies
* [BukkitOfUtils](https://modrinth.com/plugin/bukkitofutils)

## Discord
Please join the Streamline Hub Discord in order to get updates and for me to fully assist you with bugs, questions, or suggestions.

Discord: [**click here**](https://dsc.gg/streamline)

## Description
Allow players to toggle their PVP on or off. (Also enables PVP after a specified amount of grace-time.).

## Why Pacifism?
This offers a very simple configuration and setup all while remaining very light-weight.

## How to install
1. Download and install BukkitOfUtils. Found here: [BukkitOfUtils](https://modrinth.com/plugin/bukkitofutils)
2. Download the correct version of this plugin for you server version.
3. Place in your `plugins` folder.
4. Stop server.
5. Start server.
6. Use to your liking.

## More Information
### How to toggle your PVP
1. Install plugin. (Shown above.)
2. `/tpvp`

### Functions
* Disable PVP interactions:
    * Direct (melee).
    * Projectiles.
* Configurable grace-period.

### Commands
`<required>`
`(optional)`

* `/tpvp`
    * `/tpvp (player)`
        * Toggles PVP for a certain player or for yourself.
* `/spvp`
    * `/spvp <on/off> (player)`
        * Sets PVP to on / off for a certain player or for yourself.

## Configuration
### Config.yml
```YAML
player:
  # Grace Period.
  # force-toggle is the same as grace-period.
  force-toggle:
    # If grace-period is enabled.
    # true = plugin will use the grace-period.
    enabled: true
    # The time in seconds of the grace-period.
    # After this many game ticks, it will set
    # the player's pvp status to the "set-as".
    after: 18000 # 15 minutes
    # The status to set the player's pvp status
    # to after the grace-period.
    # true = player can pvp and be pvp-ed.
    set-as: true
    # The message to send to the player when
    # the grace-period is over. (When the above
    # "after" time has passed.)
    message: "&7&oYou seem fit to &c&lfight&8&o! &7&oWe have enabled your &c&lPVP&8&o!"
    # Should the plugin send the above message?
    # true = yes, send the message.
    send-message: true
  # When players are toggling PVP...
  toggle:
    # The cool-down after toggling PVP.
    cool-down:
      # If cool-down is enabled.
      enabled: true
      # This is in server ticks.
      # 20 ticks = 1 second.
      # 600 ticks = 30 seconds.
      ticks: 600

# Explosion configuration.
explosions:
  # Exploding blocks to block.
  materials:
    # The list of materials to block.
    list:
    - 'WHITE_BED'
    - 'ORANGE_BED'
    - 'MAGENTA_BED'
    - 'LIGHT_BLUE_BED'
    - 'YELLOW_BED'
    - 'LIME_BED'
    - 'PINK_BED'
    - 'GRAY_BED'
    - 'LIGHT_GRAY_BED'
    - 'CYAN_BED'
    - 'PURPLE_BED'
    - 'BLUE_BED'
    - 'BROWN_BED'
    - 'GREEN_BED'
    - 'RED_BED'
    - 'BLACK_BED'
    - 'TNT'
    - 'RESPAWN_ANCHOR'
    # The type of list to use.
    is-blacklist: false
    # The radius to check for players with pacifism on.
    radius: 15
  # Exploding entities to block.
  entities:
    # The list of entities to block.
    list:
    - 'MINECART_TNT'
    - 'PRIMED_TNT'
    - 'ENDER_CRYSTAL'
    # The type of list to use.
    is-blacklist: false
    # The radius to check for players with pacifism on.
    radius: 15

# The plugin's database settings.
database:
  # The type of database to use.
  # MYSQL = MySQL
  # SQLITE = SQLite
  # No other types are supported at this time.
  type: 'SQLITE'
  # The host or IP of the MySQL server.
  host: 'localhost'
  # The port of the MySQL server.
  port: 3306
  # The username to use to connect to the MySQL server.
  username: 'root'
  # The password to use to connect to the MySQL server.
  password: 'password'
  # The prefix to use for the tables in the database.
  table-prefix: 'pacifism_'
  # The name of the database to use (when using MySQL).
  database: 'pacifism'
  # The name of the SQLite file to use (when using SQLite).
  sqlite-file-name: 'pacifism.db'
```