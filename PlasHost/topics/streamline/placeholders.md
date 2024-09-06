# Streamline Placeholders
*This wiki page will cover various topics about the StreamlineCore placeholders and native RATAPI (Replace a Thing API).*

### Notes
StreamlineCore supports PlaceholderAPI natively -- when using the Bukkit version.

# Main Placholders
| Placeholder | Description | Example |
| ----------- | ----------- | ------- |
| `%streamline_parse_$player:::$thing%` | Parses `$thing` as `$player` | `%streamline_parse_Drakified:::*/*streamline_user_formatted*/*%` -> parses `%streamline_user_formatted%` on player `Drakified`. |
| `%streamline_?R:$thing%` | Parses `$thing` on the proxy server (Velocity or Bungeecord) or the current server if there is no proxy. | `%streamline_?R:*/*streamline_user_points*/*%` -> Parses `%streamline_user_points%` on the proxy. |