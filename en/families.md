<!-- Belgian AZERTY on Fedora, openSUSE, Arch and other Linux | https://belgian-azerty.github.io/en/families.html -->

# Belgian AZERTY on five Linux families

This project started with Linux Mint and Zorin OS. There are now also files for the other big families of Linux. It is
not equally far everywhere. Below you see how far it is for each system.

### What does the status mean?

- **Released:** there is a version to download. Tested in emulators and on one real laptop.
- **Tested in test containers:** tested in a closed-off test system without a desktop. There is nothing to download
  yet: you build the package yourself, with the steps below. A test on a real desktop will follow.
- **Script:** not a package, but a small script. Tested in test containers. Works only on desktops that use Wayland.

### The same everywhere

The same three choices as on Mint and Zorin: Caps Lock as on Windows, the Shift+AltGr accents as on Windows, and the
layout for a Belgian Apple keyboard. Ctrl+Alt as AltGr comes from keyd, with our rules.

### Different from Mint and Zorin

- No file of the system changes. Our two files go into the folder `/etc/xkb`.
- The choices do not appear in your desktop's keyboard settings. You switch them on with one command (below).
- An X11 session and the text console do not read `/etc/xkb`. Nothing changes there.


## Ubuntu and Debian

**Linux Mint 22.3 and Zorin OS 18.1: released (0.9.12).** [Go to install](https://belgian-azerty.github.io/en/install.md)

**Ubuntu 24.04 and Debian 13: the same package, tested in test containers.** Typing was tested too, on a GNOME desktop
without a screen: the same result as on Mint and Zorin. You follow the same steps as on Mint. Debian has keyd itself:
type `sudo apt install keyd` instead of using the PPA.

**Moving to Ubuntu 26.04, Linux Mint 23 or Debian 14 later?** Install 0.9.12 first. With 0.9.11 or older, the upgrade
stops half-way. Tested with a full package upgrade in test containers, not with Ubuntu's or Mint's own upgrade tools.
- [If the upgrade is already stuck: Problems](https://belgian-azerty.github.io/en/problems.md)

**On Ubuntu 26.04 (GNOME 50):** if you change a keyboard choice, such as Caps Lock or the accents, log out and back in.
Only then does the new choice work. Seen in an emulator on the test laptop.

## Fedora

**Fedora 44 and 45: tested in test containers. Fedora 45 also on a desktop in a virtual machine, with SELinux on.**

Fedora has no keyd. So these steps also build keyd 2.6.0, unchanged from the official release. Type as a normal user:

```
sudo dnf install rpm-build rpmdevtools gcc make kernel-headers systemd-rpm-macros git
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
rpmdev-setuptree
for s in packaging/fedora/*.spec; do spectool -g -R "$s" && rpmbuild -ba "$s"; done
R=$(rpm --eval %_rpmdir); sudo dnf install $R/x86_64/keyd-2.6.0-*.rpm $R/noarch/*-0.9.12-*.rpm
```

Then, in the same folder: `sudo bash be-azerty-fix.sh system`. This puts Belgian first for the whole system and for
the stored GNOME settings of your users.

**Good to know:** SELinux is on by default on Fedora. So our package adds a small SELinux rule that lets the keyboard
service read our files. Without that rule, Fedora 45 refused every layout and the login screen stayed US. With the rule,
the login screen typed Belgian, with Caps Lock as on Windows, and Ctrl+Alt+E gave €. Tested in a virtual machine on one
laptop, not on a real PC.

## openSUSE

**Tumbleweed and Leap 16.0: tested in test containers, and both on a desktop in a virtual machine, with SELinux on.**

New openSUSE installations also use SELinux. Fedora's problem did not happen on openSUSE, but our package adds the
same small rule, and it works there too. On Leap 16.0 (GNOME) the login screen typed Belgian, also after a restart. On
Tumbleweed (KDE) it works too, but at the login screen Caps Lock still works the Linux way: that screen runs on X11.
After logging in, Caps Lock works as on Windows.

openSUSE has keyd itself. Type as a normal user:

```
sudo zypper install rpm-build systemd-rpm-macros git curl
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
SRC=$(rpm --eval %_sourcedir); mkdir -p "$SRC"
curl -L -o "$SRC"/belgian-azerty-linux-0.9.12.tar.gz https://github.com/belgian-azerty/belgian-azerty-linux/archive/refs/tags/v0.9.12.tar.gz
for s in packaging/opensuse/*.spec; do rpmbuild -ba "$s"; done
sudo zypper install --allow-unsigned-rpm $(rpm --eval %_rpmdir)/noarch/*-0.9.12-*.rpm
```

Then switch the choices on (see "Switching the choices on" below).

## Arch

**Arch Linux: tested in test containers, desktop test to follow.**

Arch has keyd itself. Type as a normal user:

```
sudo pacman -S --needed base-devel git
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux/packaging/arch
(cd belgian-azerty-windows && makepkg -si)
(cd keyd-belgian-windows && makepkg -si)
```

Good to know: our keyd package switches keyd on straight away, because that is why you install it. On Arch this is
unusual.

Then switch the choices on (see below).

## Independent systems: Void, NixOS, Gentoo, Slackware, Solus

**Script: tested in test containers, X11 still open.**

Here there is no package, but a small script. It puts the same two files in `/etc/xkb` and changes nothing in the
system:

```
git clone https://github.com/belgian-azerty/belgian-azerty-linux && cd belgian-azerty-linux
sudo sh packaging/etc-xkb/be-azerty-etc-xkb.sh install
sh packaging/etc-xkb/be-azerty-etc-xkb.sh status
```

To remove: `sudo sh packaging/etc-xkb/be-azerty-etc-xkb.sh remove`. This takes out only our two files.

**Good to know**
- Tested with each system's own keyboard library and keyboard data. For Slackware and Solus there is no test
  container: their own packages were put on another test system. On Slackware 15.0 one check could not run, because the
  test tool needs a newer version.
- Only for desktops that use Wayland. An X11 session does not read `/etc/xkb`, and many of these systems still run X11
  (Slackware 15.0 by default). There is no solution for X11 yet.
- The script does not set up keyd. keyd is in Void, NixOS and Solus; on Gentoo in the GURU overlay, on Slackware on
  SlackBuilds.org. The rules for keyd are in `keyd/be-winaltgr.conf`. This was not tested here.
- On NixOS your configuration manages the `/etc` folder. Whether a rebuild leaves our files in place was not checked.

## Switching the choices on (openSUSE, Arch and the independent systems)

For the whole system, including the login screen and new users, if your system has systemd:

```
sudo localectl set-x11-keymap be pc105 "" caps:be_windows,be_azerty:accents
```

Tested in test containers. Without systemd, set the choices in your desktop's keyboard setting.

## Not yet tested outside Mint and Zorin

- A desktop on Arch and on the independent systems. The login screen is only tested on Fedora 45 and openSUSE, in a
  virtual machine. KDE Plasma only on Tumbleweed.
- keyd in daily use.
- The text console and the disk unlock screen.
- A real installation or a real PC.

All details: [packaging/OTHER-DISTRIBUTIONS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/packaging/OTHER-DISTRIBUTIONS.md) and [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Does it work for you, or not quite?** Tell us on [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions). Every test on a real computer helps.

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
