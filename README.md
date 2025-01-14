# Verifying files

To download `SHASUMS256.txt` using curl:

```
curl -O https://get.pnpm.io/SHASUMS256.txt
```

To check that a downloaded file matches the checksum, run it through sha256sum with a command such as:

```
grep v6.16.js SHASUMS256.txt | sha256sum -c -
```

The GPG detached signature of `SHASUMS256.txt` is in `SHASUMS256.txt.sig`.
You can use it with `gpg` to verify the integrity of `SHASUMS256.txt`.
You will first need to import the GPG keys of individuals authorized to create releases.
To import the keys:

```
curl https://keybase.io/pnpm/pgp_keys.asc | gpg --import
```

Next, download the `SHASUMS256.txt.sig`:

```
curl -O https://get.pnpm.io/SHASUMS256.txt.sig
```

Then use the following script to verify the file's signature:

```
gpg --verify SHASUMS256.txt.sig SHASUMS256.txt
```
