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

## Commands
### Definitions
`<required>` - "required" (literal) is required for the command to work.
`(optional)` - "optional" (literal) is optional for the command to work.
`"thing"` - thing is non-literal; meaning you specify something that "thing" describes. Such as a world name, or player name.

* `/tpvp`
    * `/tpvp ("player") (-f)`
        * Toggles PVP for a certain player or for yourself.
        * Use `-f` to force toggling; meaning it will bypass the cooldown.
* `/spvp`
    * `/spvp <on/off> ("player") (-f)`
        * Sets PVP to on / off for a certain player or for yourself.
        * Use `-f` to force setting; meaning it will bypass the cooldown.
* `/worldwhitelist`
    * `/worldwhitelist <set-as> <whitelist|blacklist>`
        * Sets the whitelist to either be a **whitelist** (worlds in it are the only worlds that Pacifism works in) or a **blacklist** (worlds in it are excluded from Pacifism working in them).
    * `/worldwhitelist <add/remove> ["world"]`
        * Adds a world to the whitelist/blacklist.
    * `/worldwhitelist <list>`
        * Lists all worlds currently in the whitelist/blacklist.
* `/setgracetime`
    * `/setgracetime <"ticks"> ["player"]`
        * Sets the gracetime in ticks for a certain player or for yourself.

## Permissions
- `pacifism.command.togglepvp` - Allows running the command `/tpvp`.
- `pacifism.command.setpvp` - Allows running the command `/spvp`.
- `pacifism.command.worldwhitelist` - Allows running the command `/worldwhitelist`.
- `pacifism.command.setgracetime` - Allows running the command `/setgracetime`.
- `pacifism.others.toggle` - Allows toggling other players' PVP.
- `pacifism.others.set` - Allows setting other players' PVP to on or off.
- `pacifism.others.gracetime` - Allows setting other players' gracetime.
- `pacifism.force` - Allows toggling or setting PVP forcefully (bypasses cooldown).

## Placeholders
*You can use* [**PlaceholderAPI**](https://www.spigotmc.org/resources/6245/) *to use Pacifism's placeholders in other areas of your server!*
#### Our Placeholders
| Placeholder                                                         | Description                                                                                                              |
|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| `%pacifism_gracetime_left_ticks%`                                   | The amount of ticks (typically, 20 ticks = 1 second) left until the player has their pvp toggled. This shows an integer. |
| `%pacifism_gracetime_left_ticks_fancy%`                             | Shows the ticks left, but in the fancy format you configured in the plugin's config.                                     |
| `%pacifism_gracetime_left_seconds%`                                 | The amount of seconds left until the player has their pvp toggled. This shows an integer.                                |
| `%pacifism_gracetime_left_seconds_fancy%`                           | Shows the seconds left, but in the fancy format you configured in the plugin's config.                                   |
| `%pacifism_status_simple%`                                          | The status of the player's PVP. This will show either "true" or "false".                                                 |
| `%pacifism_status_fancy%`                                           | The status of the player's PVP. This will show the value you set in the config depending on if it is true or false.      |
| `%pacifism_as_<player>_<one of the above without the "pacifism_">%` | Does the above, but as `<player>`. Remember to replace the fields between the `<` and the `>` for both arguments.        |

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
    # Countdown configuration.
    countdown:
      # If countdown is enabled.
      enabled: true
      # Commands to run at x ticks left.
      commands:
        '6000':
          - '(message) %player_name% &7&oYou have &a&o5 &f&ominutes &7&oleft of your grace period.'
        '1200':
          - '(message) %player_name% &7&oYou have &a&o1 &f&ominute &7&oleft of your grace period.'
        '600':
          - '(message) %player_name% &7&oYou have &a&o30 &f&oseconds &7&oleft of your grace period.'
        '300':
          - '(message) %player_name% &7&oYou have &a&o15 &f&oseconds &7&oleft of your grace period.'
        '100':
          - '(message) %player_name% &7&oYou have &a&o5 &f&oseconds &7&oleft of your grace period.'
        '80':
          - '(message) %player_name% &a&o4 &f&oseconds&7&o...'
        '60':
          - '(message) %player_name% &a&o3 &f&oseconds&7&o...'
        '40':
          - '(message) %player_name% &a&o2 &f&oseconds&7&o...'
        '20':
          - '(message) %player_name% &a&o1 &f&osecond&7&o...'
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

# PlaceholderAPI configuration.
placeholders:
  # Grace Period placeholders.
  gracetime:
    # Placeholder for the grace time left.
    left:
      # The time in ticks.
      ticks:
        # The simple placeholder.
        simple: "%gracetime_left_ticks%"
        # The fancy placeholder.
        fancy: "&a%gracetime_left_ticks% &fticks"
      # The time in seconds.
      seconds:
        # The simple placeholder.
        simple: "%gracetime_left_seconds%"
        # The fancy placeholder.
        fancy: "&a%gracetime_left_seconds% &fseconds"
  # PVP status placeholders.
  status:
    # Placeholder for when PVP is toggled off.
    pvp-off:
      # The simple placeholder.
      # '%status_pvp%' will be replaced with the
      # status of the player's PVP. (true/false)
      simple: "%status_pvp%"
      # The fancy placeholder.
      fancy: "&c&lOFF"
    # Placeholder for when PVP is toggled on.
    pvp-on:
      # The simple placeholder.
      # '%status_pvp%' will be replaced with the
      # status of the player's PVP. (true/false)
      simple: "%status_pvp%"
      # The fancy placeholder.
      fancy: "&a&lON"

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