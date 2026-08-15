# homebrew-snooze

Homebrew tap for [snooze](https://github.com/rtulke/snooze) — temporarily mute Zabbix
hosts and hostgroups.

## Install

```sh
brew install rtulke/snooze/snooze
```

The fully qualified name is required. Homebrew's core repository already ships an
unrelated tool also called [`snooze`](https://github.com/leahneukirchen/snooze) — a small
cron replacement — and core takes precedence over a tap for a bare formula name, so
`brew install snooze` installs *that* one even after `brew tap rtulke/snooze`.

If `snooze help` hangs instead of printing help, you have the other tool:

```sh
brew uninstall snooze               # removes homebrew-core's snooze
brew install rtulke/snooze/snooze
```

Both provide a `snooze` binary, so only one can be linked at a time.

## Upgrade

```sh
brew update && brew upgrade rtulke/snooze/snooze
```

## Usage

snooze needs a Zabbix API token before it can do anything beyond
`--help`/`--version`:

```sh
cp "$(brew --prefix rtulke/snooze/snooze)/share/doc/snooze/snooze.conf.example" ~/.snooze.conf
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
