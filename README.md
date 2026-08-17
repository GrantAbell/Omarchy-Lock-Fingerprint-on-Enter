# Omarchy Lockscreen Fingerprint on Enter

An Omarchy 4 lock screen plugin which allows for fingerprint reader re-activation by pressing the enter key when no password has been typed. Ideal for fingerprint readers that trigger libfprint's overheating protection when left active for too long.

## What it does

By default, Omarchy automatically restarts fingerprint authentication after it times out. Some fingerprint readers don't handle this well and can eventually hit:

```text
Device disabled to prevent overheating.
```

This plugin changes the lock screen behavior so that:

* The fingerprint reader activates normally when the screen is locked.
* After the default 30-second fingerprint timeout, the reader turns off and stays off.
* Pressing **Enter** with an empty password field starts a new fingerprint attempt.
* Password authentication continues to work normally.

This gives the reader time to remain inactive instead of immediately starting another fingerprint session.

## Who is this for?

This is intended for Omarchy users whose fingerprint reader works normally, but gets disabled by libfprint's overheating protection when the lock screen keeps fingerprint authentication running or repeatedly restarts it.

If your fingerprint reader works fine with Omarchy's default lock screen behavior, you don't need this plugin.

## Installation

```bash
omarchy plugin add https://github.com/GrantAbell/Omarchy-Lock-Fingerprint-on-Enter.git
```

Enable the plugin when prompted, then restart the Omarchy shell if necessary:

```bash
omarchy-restart-shell
```

## Removal

```bash
omarchy plugin remove grantabell.lock-fingerprint-on-enter
```

Removing the plugin restores Omarchy's built-in lock screen.

## Usage

Lock your screen normally. The fingerprint reader will activate for the initial authentication period.

If it times out, press **Enter** while the password field is empty to activate the fingerprint reader again.

Typing a password and pressing Enter still performs normal password authentication.

## Requirements

* Omarchy 4 / Quattro
* `fprintd` with an enrolled fingerprint
* A working `/etc/pam.d/omarchy-lock-fingerprint` configuration

## License

MIT

---

*This plugin was developed with AI assistance. Its lock screen code is derived from Omarchy's built-in lock plugin.*
