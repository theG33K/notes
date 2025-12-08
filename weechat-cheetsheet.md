# My Personal WeeChat Cheat Sheet

## Requirements

You need at least WeeChat 3.2-dev

## Install

### Ubuntu/Debian

```sh
$ sudo apt-key adv --keyserver hkps://keys.openpgp.org --recv-keys 11E9DE8848F2B65222AA75B8D1820DB22A11534E
$ echo "deb https://weechat.org/ubuntu focal main" | sudo tee /etc/apt/sources.list.d/weechat.list
$ echo "deb-src https://weechat.org/ubuntu focal main" | sudo tee -a /etc/apt/sources.list.d/weechat.list
$ sudo apt-get update
$ sudo apt-get install weechat-curses weechat-plugins weechat-python weechat-perl
```

### macOs

```
$ brew install weechat
```

## Default Files Location

| Path | Description |
| --- | --- |
| `~/.config/weechat` | WeeChat configuration files: `*.conf`, certificates, etc. |
| `~/.local/share/weechat` | WeeChat data files: logs, scripts, scripts data, xfer files, etc. |
| `~/.cache/weechat` | WeeChat cache files: scripts cache. |


## Network

### Secured data

#### Generate the Key and Certificate

```sh
$ openssl req \
  -nodes \
  -new \
  -newkey rsa:2048 \
  -keyout nick.key \
  -x509 \
  -days 3650 \
  -out nick.cer \
  -subj "/C=UK/ST=Kyiv-Oblast/L=Irpen/O=Home/emailAddress=egrep@protonmail.ch"
  
$ chmod 400 nick.*

$ cat nick.cer nick.key > nick.pem

$ chmod 400 nick.pem
```

#### Copy Certs

```sh
$ mkdir -p ~/.config/weechat/certs
$ mv nick.{key,cer,pem} ~/.config/weechat/certs
```

#### Set Passphrase

```
/secure set oftc ********
/secure set libera ********
```

### Default settings

```
/set irc.server_default.sasl_mechanism PLAIN
/set irc.server_default.sasl_username serghei
# variants of nickname to use
/set irc.server_default.nicks "serghei,serghei1,serghei2,serghei3"
/set irc.server_default.realname "Serghei Iakovlev"
/set irc.server_default.capabilities "account-notify,away-notify,cap-notify,multi-prefix,server-time,znc.in/self-message"
```

the last line request some IRCv3 capabilities. Capabilities supported by WeeChat are: account-notify, away-notify, cap-notify, extended-join, multi-prefix, server-time, userhost-in-names. See [IRCv3 Specifications](http://ircv3.net/irc/) to learn more about IRCv3 capabilities.

Note: OFTC dooes not support SASL yet.

### Network-specific settings

```
# oftc
/server add oftc irc.oftc.net/6697 -ssl -ssl_verify -autoconnect
/set irc.server.oftc.ssl_cert %h/certs/nick.pem
/set irc.server.oftc.command_delay 5
/set irc.server.oftc.command "/msg nickserv identify ${sec.data.oftc}"
/set irc.server.oftc.autojoin #re2c

# libera.chat
/server add libera.chat irc.libera.chat/6697 -ssl -autoconnect
/set irc.server.libera.chat.autojoin #re2c,#sway,#django,#gentoo
/set irc.server.libera.chat.sasl_password ${sec.data.libera}
```

### Plugins

```
/set script.scripts.download_enabled on
```

#### Load at startup

```
/set weechat.plugin.autoload "*,!guile,!javascript,!php,!tcl,!lua,!ruby,!fifo,!xfer"
```

The following plugins are disabled:


| Plugun | Description |
| --- | --- |
| `guile` | Guile (scheme) scripting API. |
| `javascript` | JavaScript scripting API. |
| `php` | PHP scripting API. |
| `tcl` | Tcl scripting API. |
| `lua` | Lua scripting API. |
| `ruby` | Ruby scripting API. |
| `fifo` | FIFO pipe used to remotely send commands to WeeChat. |
| `xfer` | File transfer and direct chat. |

#### Logger

```
# don't log the core weechat application
/set logger.level.core.weechat 0

# log channels and messages to me
/set logger.level.irc 1

# location of logs - with year
/set logger.mask.irc %Y/$server/$channel.%m-%d.log

# Put brackets around the Nickname so it's different from the message
/set logger.file.nick_suffix "]"
/set logger.file.nick_prefix "["
```

## Bars

### Bar buflist and control_buffers

```
/bar set buflist priority 2000
```

```
/script install autosort.py

# show servers as individual buffers
/set irc.look.server_buffer independent
```

### Bar Nicklist

```
/set weechat.bar.nicklist.separator on
/set weechat.bar.nicklist.conditions "${nicklist} && ${window.number} == 1"
/set weechat.bar.nicklist.size_max 20
/set weechat.bar.nicklist.size 16
```

## Filters

```
# filter out join/part/quit/nick messages from inactive users
/filter add irc_smart * irc_smart_filter *
/set irc.look.smart_filter on
```

## Security

### Disable CTCP

```
# switch of things we don't need and provide less information
/set irc.ctcp.clientinfo ""
/set irc.ctcp.finger ""
/set irc.ctcp.source ""
/set irc.ctcp.time ""
/set irc.ctcp.userinfo ""
/set irc.ctcp.version ""
/set irc.ctcp.ping "
```

### Remove WeeChat version part/quit messages

```
/set irc.server_default.msg_part ""
/set irc.server_default.msg_quit ""
```

## Appearance 

```
# whether a line where you have been mentioned is highlighted
/script install colorize_lines.pl
/set plugins.var.perl.colorize_lines.hightlight on

# Nick are coloured
/set irc.look.color_nicks_in_nicklist on

# Use a different color for offline Nicks
/set weechat.look.color_nick_offline yes

# if it's the same person talking don't repeat their name as a prefix either
# use a space or a return symbol to show it's still them speaking
/set weechat.look.prefix_same_nick "⤷"
/set weechat.look.prefix_suffix "│"
/set weechat.look.prefix_action " •"
/set weechat.look.read_marker_string "─"
/set weechat.look.separator_horizontal ""
/set weechat.look.prefix_network "▬▬"

# increase colours available to use in Nicks
/set weechat.color.chat_nick_colors "1,2,3,4,6,7,9,10,11,12,13,14,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,69,70,71,72,73,74,75,76,77,78,79,80,81,82,83,84,85,86,87,88,89,90,182,183,184,244,225,226,227"

/set weechat.color.chat_host cyan

# Using solarized terminal which has a dark background.
# This sets background of the highlight to be dark and the star means the text is bolded.
# The text itself is highlighted in orange/pink.
/set weechat.color.chat_highlight *16
/set weechat.color.chat_highlight_bg 9
```

## Key Bindings

```
# alt-b to toggle the buflist
/key bind meta-b /bar toggle buflist

/key bind meta-, /window scroll_up
/key bind meta-. /window scroll_down
```
