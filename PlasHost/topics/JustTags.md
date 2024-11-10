# JustTags Setup (JTags)
## Creating Tags
**Command:**
<br>
```/jtags create <identifier> <format>```

**Explanation**:
<br>
The `<identifier>` is what you want the plugin to call the tag. This is not what is displayed. This is only for the plugin's internals and assigning it to players.
<br>
The `format` is what you want the tag to look like when players are using it.
<br>
<br>
***NOTE:*** *This is usually prepended with* `&r ` (notice the space) *so that there is a space between the player's rank and the tag.* (If using as a suffix. If you are using it as a prefix, `&r ` will be **appended** *not* prepended to the tag's format.)

## Assigning Tags to Players
**Command:**
<br>
```/jtags grant <identifier>```
*This only grants it to them, they still need to equip it.*

## Using (Equipping) the Tag
***NOTE:*** *The player equipping the tag, needs to have the tag granted to them before they can use it!*
<br>
<br>
**Command:**
<br>
```/jtags equip <identifier>```
**Extra Information:**
You can allow players to equip more than one tag. This includes the ability for them to arrange them how they like.

## Server-Side Setup
*This is the setup you will need to do in the server files.*
- You must have PlaceholderAPI installed.
- The placeholder for a player's tag is `%jtags_container%` and includes all equipped tags that are usable -- usable, meaning that they have permissions to have that many tags.
- Any tab management, scoreboard management, or chat management plugin you have needs to use this placeholder (if you want it to be used in those areas.