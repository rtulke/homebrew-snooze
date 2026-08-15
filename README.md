# homebrew-snooze

Homebrew tap for [snooze](https://github.com/rtulke/snooze) — temporarily mute Zabbix
hosts and hostgroups.

## Install

```sh
brew tap rtulke/snooze
brew install snooze
```

## Upgrade

```sh
brew update && brew upgrade snooze
```

## Usage

snooze needs a Zabbix API token before it can do anything beyond
`--help`/`--version`:

```sh
cp "$(brew --prefix snooze)/share/doc/snooze/snooze.conf.example" ~/.snooze.conf
$EDITOR ~/.snooze.conf   # set url + token
```

Basic examples:

```sh
# Mute the local host for the default duration
snooze

# Mute a host for 2h
snooze 2h prd-mail-5

# Mute a hostgroup for 2h
snooze 2h "@Servers/Linux"

# Remove a mute
snooze unmute prd-mail-5
```

See `man snooze` or `snooze --help` for all commands, and the
[full documentation](https://github.com/rtulke/snooze#readme) for
configuration, target syntax (globs/regex/hostgroups), scheduled starts
(`snooze plan`), and the bilingual German/English output.

## Source

Formula source: [rtulke/snooze](https://github.com/rtulke/snooze/blob/main/Formula/snooze.rb)
