<!-- Check your download with SHA256SUMS | https://belgian-azerty.github.io/en/verify.html -->

# Is your download correct?

Every version comes with a **SHA256SUMS** file. It holds the fingerprint of each file. If your fingerprint matches,
your file was not changed on the way.

**On Linux**, in the folder with the files:

```
sha256sum -c SHA256SUMS --ignore-missing
```

Every file must show **OK**.

**On Windows** (PowerShell), one file at a time:

```
Get-FileHash .\belgian-azerty-windows_0.9.10_all.deb -Algorithm SHA256
```

Compare the long code with the line for that file in SHA256SUMS.

**Doesn't it match?** Then don't use the file. Download it again from the [release page](https://github.com/belgian-azerty/belgian-azerty-linux/releases/latest).

---

Built with AI help (Claude). Not affiliated with Linux Mint or Zorin OS. A small volunteer project.
