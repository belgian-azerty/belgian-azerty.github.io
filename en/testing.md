<!-- What is tested for Mint 22.3 and Zorin 18.1 | https://belgian-azerty.github.io/en/testing.html -->

# What is tested, and what is not

**Tested**
- Linux Mint 22.3 and Zorin OS 18.1, in emulators and on one laptop (a Lenovo ThinkPad T14s).
- The changes in 0.9.10, 0.9.11 and 0.9.12 themselves: only in test containers. 0.9.12 types the same as 0.9.11.
- Mint 0.9.9 as a USB stick on the real laptop (reported by Younes).
- Windows and Linux compared: with both accent options, 306 of the 308 Belgian Windows characters match. The last two
  are AltGr+4 and AltGr+5, and keyd handles those.
- Ubuntu 24.04 and Debian 13 in test containers, including typing on a GNOME desktop without a screen: the same result
  as on Mint and Zorin.
- A full package upgrade from Ubuntu 24.04 to 26.04 and from Debian 13 to the next Debian, in test containers.
- Fedora, openSUSE, Arch, Void, NixOS, Gentoo, Slackware and Solus: in test containers, without a desktop.
  [Five Linux families](https://belgian-azerty.github.io/en/families.md)
- Fedora 45 and openSUSE Leap 16.0 on a desktop in a virtual machine, with SELinux on: the login screen types
  Belgian, with Caps Lock as on Windows.
- openSUSE Tumbleweed with KDE in a virtual machine, with SELinux on: the login screen types Belgian, but with Caps
  Lock the Linux way (X11). After logging in, as on Windows.

**Not yet tested**
- A real Apple keyboard.
- 0.9.10 to 0.9.12, and Zorin 0.9.9, on real hardware.
- Ubuntu's and Mint's own upgrade tools.
- Systems other than Mint and Zorin on a real desktop or a real PC.
- A second USB keyboard.

**Status with the Linux projects:** nothing accepted yet. Which part belongs to which project is in [MAINTAINERS.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/MAINTAINERS.md).

All details, with the version for each test: [HOW-WE-TESTED.md](https://github.com/belgian-azerty/belgian-azerty-linux/blob/main/HOW-WE-TESTED.md).

**Want to help?** Test with us or answer the poll on [GitHub Discussions](https://github.com/belgian-azerty/belgian-azerty-linux/discussions).

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
