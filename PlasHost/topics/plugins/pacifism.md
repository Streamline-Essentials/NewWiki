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
* `<required>` - "required" (literal) is required for the command to work.
* `(optional)` - "optional" (literal) is optional for the command to work.
* `"thing"` - thing is non-literal; meaning you specify something that "thing" describes. Such as a world name, or player name.

### Plugin Commands
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

#### Time Units
Use these as a key for the below placeholders.

| Time Unit | Description            | Notes                 |
|-----------|------------------------|-----------------------|
| `ticks`   | The time in ticks.     | 20 ticks per 1 second |
| `seconds` | The time in seconds.   |                       |
| `minutes` | The time in minutes.   |                       |
| `hours`   | The time in hours.     |                       |
| `days`    | The time in days.      |                       |
| `weeks`   | The time in weeks.     |                       |

#### Our Placeholders
| Placeholder                                                     | Description                                                                                                         | Examples                                             |
|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| `%pacifism_gracetime_left_<time unit>%`                         | The amount of <time unit> left until the player has their pvp toggled. This shows an integer.                       | 120 ticks: `120`<br/>142 ticks: `7.1`                |
| `%pacifism_gracetime_left_<time unit>_fancy%`                   | Shows the <time unit> left, but in the fancy format you configured in the plugin's config.                          | 6000 ticks: `5 minutes`<br/>65 ticks: `3.25 seconds` |
| `%pacifism_gracetime_left_combined%`                            | Will show the full and formatted amount of grace time left.                                                         | 1221 ticks: `1 minute 1 second 1 tick`               |
| `%pacifism_cooldown_left_<time unit>%`                          | The amount of <time unit> left until the player can toggle their pvp again (to enabled). This shows an integer.     | 120 ticks: `120`<br/>142 ticks: `7.1`                |
| `%pacifism_cooldown_left_<time unit>_fancy%`                    | Shows the <time unit> left, but in the fancy format you configured in the plugin's config.                          | 6000 ticks: `5 minutes`<br/>65 ticks: `3.25 seconds` |
| `%pacifism_cooldown_left_combined%`                             | Will show the full and formatted amount of toggle cooldown left.                                                    | 1221 ticks: `1 minute 1 second 1 tick`               |
| `%pacifism_status_simple%`                                      | The status of the player's PVP. This will show either "true" or "false".                                            | `true`<br/>`false`                                   |
| `%pacifism_status_fancy%`                                       | The status of the player's PVP. This will show the value you set in the config depending on if it is true or false. | `ON`<br/>`OFF`                                       |
| `%pacifism_as_<player>_<one of the above without "pacifism_">%` | Does the above, but as `<player>`. Remember to replace the fields between the `<` and the `>` for both arguments.   | `%pacifism_as_Drakified_status_simple%`              |

#### Formatting your Placeholders
Use the following placeholders in your `placeholders` config section to format the output.

| Placeholder                                                | Description                                                                       |
|------------------------------------------------------------|-----------------------------------------------------------------------------------|
| `%gracetime_left_<time unit>%`                             | The time left in <time unit> rounded down                                         |
| `%gracetime_left_<time unit>_full%`                        | The time left in <time unit> with decimals                                        |
| `%gracetime_left_<time unit>_truncated:<places>%`          | The time left in <time unit> truncated to <places> decimal places.                |
| `%cooldown_left_<time unit>%`                              | The toggle cooldown left in <time unit> rounded down                              |
| `%cooldown_left_<time unit>_full%`                         | The toggle cooldown left in <time unit> with decimals                             |
| `%cooldown_left_<time unit>_truncated:<places>%`           | The toggle cooldown left in <time unit> truncated to <places> decimal places.     |

## Configuration
### `config.yml`
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
      # Negative grace time.
      negatives:
        # If the plugin should replace the negative time.
        # true = replace the negative time.
        # false = do not replace the negative time.
        replace: true
        # What to replace the negative time with.
        replace-to: 0
      # The below have the following options:
      # %gracetime_left_ticks% = The time left in ticks rounded down.
      # %gracetime_left_ticks_full% = The time left in ticks with decimals.
      # %gracetime_left_ticks_truncated:<places>% = The time left in ticks truncated to <places> decimal places.
      # %gracetime_left_seconds% = The time left in seconds rounded down.
      # %gracetime_left_seconds_full% = The time left in seconds with decimals.
      # %gracetime_left_seconds_truncated:<places>% = The time left in seconds truncated to <places> decimal places.
      # %gracetime_left_minutes% = The time left in minutes rounded down.
      # %gracetime_left_minutes_full% = The time left in minutes with decimals.
      # %gracetime_left_minutes_truncated:<places>% = The time left in minutes truncated to <places> decimal places.
      # %gracetime_left_hours% = The time left in hours rounded down.
      # %gracetime_left_hours_full% = The time left in hours with decimals.
      # %gracetime_left_hours_truncated:<places>% = The time left in hours truncated to <places> decimal places.
      # %gracetime_left_days% = The time left in days rounded down.
      # %gracetime_left_days_full% = The time left in days with decimals.
      # %gracetime_left_days_truncated:<places>% = The time left in days truncated to <places> decimal places.
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
      # The time in minutes.
      minutes:
        # The simple placeholder.
        simple: "%gracetime_left_minutes%"
        # The fancy placeholder.
        fancy: "&a%gracetime_left_minutes% &fminutes"
      # The time in hours.
      hours:
        # The simple placeholder.
        simple: "%gracetime_left_hours%"
        # The fancy placeholder.
        fancy: "&a%gracetime_left_hours% &fhours"
      # The time in days.
      days:
        # The simple placeholder.
        simple: "%gracetime_left_days%"
        # The fancy placeholder.
        fancy: "&a%gracetime_left_days% &fdays"
      # The time in days.
      weeks:
        # The simple placeholder.
        simple: "%gracetime_left_weeks%"
        # The fancy placeholder.
        fancy: "&a%gracetime_left_weeks% &fweeks"
      # The time combined placeholder.
      combined:
        # Uses the fancy placeholders for each time unit - listed above.
        # NOTE: All leading and trailing spaces will be removed.
        # Options:
        # %days% = days section.
        # %hours% = hours section.
        # %minutes% = minutes section.
        # %seconds% = seconds section.
        # %ticks% = ticks section.
        fancy: "%weeks% %days% %hours% %minutes% %seconds% %ticks%"
        sections:
          only-show-if-not-zero: true
          weeks: "&a%amount% &fweeks"
          days: "&a%amount% &fdays"
          hours: "&a%amount% &fhours"
          minutes: "&a%amount% &fminutes"
          seconds: "&a%amount% &fseconds"
          ticks: "&a%amount% &fticks"
  # Cooldown placeholders.
  cooldown:
    # Placeholder for the grace time left.
    left:
      # Negative grace time.
      negatives:
        # If the plugin should replace the negative time.
        # true = replace the negative time.
        # false = do not replace the negative time.
        replace: true
        # What to replace the negative time with.
        replace-to: 0
      # The below have the following options:
      # %cooldown_left_ticks% = The time left in ticks rounded down.
      # %cooldown_left_ticks_full% = The time left in ticks with decimals.
      # %cooldown_left_ticks_truncated:<places>% = The time left in ticks truncated to <places> decimal places.
      # %cooldown_left_seconds% = The time left in seconds rounded down.
      # %cooldown_left_seconds_full% = The time left in seconds with decimals.
      # %cooldown_left_seconds_truncated:<places>% = The time left in seconds truncated to <places> decimal places.
      # %cooldown_left_minutes% = The time left in minutes rounded down.
      # %cooldown_left_minutes_full% = The time left in minutes with decimals.
      # %cooldown_left_minutes_truncated:<places>% = The time left in minutes truncated to <places> decimal places.
      # %cooldown_left_hours% = The time left in hours rounded down.
      # %cooldown_left_hours_full% = The time left in hours with decimals.
      # %cooldown_left_hours_truncated:<places>% = The time left in hours truncated to <places> decimal places.
      # %cooldown_left_days% = The time left in days rounded down.
      # %cooldown_left_days_full% = The time left in days with decimals.
      # %cooldown_left_days_truncated:<places>% = The time left in days truncated to <places> decimal places.
      # The time in ticks.
      ticks:
        # The simple placeholder.
        simple: "%cooldown_left_ticks%"
        # The fancy placeholder.
        fancy: "&a%cooldown_left_ticks% &fticks"
      # The time in seconds.
      seconds:
        # The simple placeholder.
        simple: "%cooldown_left_seconds%"
        # The fancy placeholder.
        fancy: "&a%cooldown_left_seconds% &fseconds"
      # The time in minutes.
      minutes:
        # The simple placeholder.
        simple: "%cooldown_left_minutes%"
        # The fancy placeholder.
        fancy: "&a%cooldown_left_minutes% &fminutes"
      # The time in hours.
      hours:
        # The simple placeholder.
        simple: "%cooldown_left_hours%"
        # The fancy placeholder.
        fancy: "&a%cooldown_left_hours% &fhours"
      # The time in days.
      days:
        # The simple placeholder.
        simple: "%cooldown_left_days%"
        # The fancy placeholder.
        fancy: "&a%cooldown_left_days% &fdays"
      # The time in days.
      weeks:
        # The simple placeholder.
        simple: "%cooldown_left_weeks%"
        # The fancy placeholder.
        fancy: "&a%cooldown_left_weeks% &fweeks"
      # The time combined placeholder.
      combined:
        # Uses the fancy placeholders for each time unit - listed above.
        # NOTE: All leading and trailing spaces will be removed.
        # Options:
        # %days% = days section.
        # %hours% = hours section.
        # %minutes% = minutes section.
        # %seconds% = seconds section.
        # %ticks% = ticks section.
        fancy: "%weeks% %days% %hours% %minutes% %seconds% %ticks%"
        sections:
          only-show-if-not-zero: true
          weeks: "&a%amount% &fweeks"
          days: "&a%amount% &fdays"
          hours: "&a%amount% &fhours"
          minutes: "&a%amount% &fminutes"
          seconds: "&a%amount% &fseconds"
          ticks: "&a%amount% &fticks"
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

### `messages.yml`
```YAML
# Placeholders used for a player's PVP status being toggled.
status:
  enabled: "&aenabled"
  disabled: "&cdisabled"

###########################################
# Global (all) feedback message features:
# Setting the value as blank ("") will
# disable the feedback message completely.
###########################################

# Feedback messages for when a player's PVP is toggled.
toggle:
  success:
    self:
      self: "&eYou have %status% &eyour PVP&8!"
      upon:
        enable: "&7(You will be able to take damage from other players.)"
        disable: "&7(You will not be able to take damage from other players.)"
    other:
      self: "&eYou have %status% &b%player_name%&e's PVP&8!"
      other: "&eYour PVP has been %status% &eby &b%player_name%&8!"
      upon:
        enable: "&7(They will be able to take damage from other players.)"
        disable: "&7(They will not be able to take damage from other players.)"
  cannot:
    self:
      self: "&cYou cannot toggle your PVP&8!"
      time-left: "&cYou have &f%cooldown_left_seconds% &cseconds left before you can toggle your PVP again&8!"
    other:
      self: "&cYou cannot toggle &b%player_name%&c's PVP&8!"
      time-left: "&cThey have &f%cooldown_left_seconds% &cseconds left before they can toggle their PVP again&8!"

# Feedback messages for when a player's PVP is set.
set:
  success:
    self:
      self: "&eYou have %status% &eyour PVP&8!"
      upon:
        enable: "&7(You will be able to take damage from other players.)"
        disable: "&7(You will not be able to take damage from other players.)"
    other:
      self: "&eYou have %status% &b%player_name%&e's PVP&8!"
      other: "&eYour PVP has been %status% &eby &b%player_name%&8!"
      upon:
        enable: "&7(They will be able to take damage from other players.)"
        disable: "&7(They will not be able to take damage from other players.)"
  cannot:
    self:
      self: "&cYou cannot toggle your PVP&8!"
      time-left: "&cYou have &f%cooldown_left_seconds% &cseconds left before you can toggle your PVP again&8!"
    other:
      self: "&cYou cannot toggle &b%player_name%&c's PVP&8!"
      time-left: "&cThey have &f%cooldown_left_seconds% &cseconds left before they can toggle their PVP again&8!"

# Feedback messages for when a player's grace-time is set.
set-grace-time:
  success:
    self:
      self: "&eYou have set your grace-time to &b%gracetime_left_seconds% &eseconds&8!"
    other:
      self: "&eYou have set &b%player_name%&e's grace-time to &b%gracetime_left_seconds% &eseconds&8!"
      other: "&eYour grace-time has been set to &b%gracetime_left_seconds% &eseconds&8!"

# Feedback messages for when a player tries to hurt another player.
pvp:
  disabled:
    self: "&cYou have PVP disabled! You cannot hurt other players."
    other: "&cThat player has PVP disabled! You cannot hurt them."
```