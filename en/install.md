<!-- Install on Linux Mint 22.3 and Zorin OS 18.1 | https://belgian-azerty.github.io/en/install.html -->

# Install on a system that is already running

For Linux Mint 22.3 and Zorin OS 18.1. You type something into a terminal three times.

## Step 1. Add keyd.

keyd is the program that makes Ctrl+Alt work as AltGr. Ubuntu 24.04, the base of Mint 22 and
Zorin 18, does not have it. The keyd-team PPA does. That PPA is run by the maintainer of Debian's keyd package; it is
not part of the keyd project itself.

```
sudo add-apt-repository ppa:keyd-team/ppa
sudo apt update
sudo apt install keyd
```

## Step 2. Install our two packages.

Download them from the [0.9.10 release page](https://github.com/belgian-azerty/belgian-azerty-linux/releases/tag/v0.9.10) into an empty folder. Open a
terminal there and type:

```
sudo apt install ./keyd-belgian-windows_0.9.10_all.deb ./belgian-azerty-windows_0.9.10_all.deb
sudo be-azerty-fix system
```

Want a comma on the numeric keypad? Then type `sudo DECIMAL=comma be-azerty-fix system`.

## Step 3. Log out and log back in.

`be-azerty-fix check` shows what each setting says.

**Prefer clicking?** After installing, the menu has a **Belgian keyboard** entry. There you choose between the Windows
profile and the Linux profile, with a period or a comma.

**Good to know**
- The Ctrl+Alt rules apply to every keyboard you plug in, including an external US keyboard.
- On Zorin, Caps Lock stays as on Linux by default. That is because of a GNOME bug with password windows. You can
  switch on the Windows Caps Lock yourself. [Explained in the README](https://github.com/belgian-azerty/belgian-azerty-linux#caps-lock-on-zorin)
- All known problems are in the [README, under "Known issues"](https://github.com/belgian-azerty/belgian-azerty-linux#known-issues).

- [Check your download first](https://belgian-azerty.github.io/en/verify.md)

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
