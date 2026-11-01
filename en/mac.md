<!-- Belgian Apple keyboard on Linux Mint and Zorin OS | https://belgian-azerty.github.io/en/mac.html -->

# A Belgian Apple keyboard

A Belgian Apple keyboard has different characters printed on it than a PC keyboard, for example @ left of the 1. With
the PC layout, many keys then type something else. If you use such a keyboard, type this after installing:

```
sudo APPLE=yes be-azerty-fix system
```

Are the key left of the 1 and the key next to the left Shift swapped? Then also type:

```
sudo be-azerty-fix apple-iso-keys on
```

**Good to know**
- Option works as AltGr. Caps Lock works as on Linux.
- The setting applies to every keyboard on the computer, including on the login screen. That is why it refuses when no
  Apple keyboard is plugged in.
- The text console and the disk unlock screen keep the PC layout.
- **Not yet tested on a real Apple keyboard.** In a test container, 333 of the 367 macOS characters matched. The
  difference is Caps Lock, which works differently on a Mac.

Back to a PC keyboard: `sudo APPLE=no be-azerty-fix system`.

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
