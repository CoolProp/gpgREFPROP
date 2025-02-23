Following the instructions from https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions, a zip file called ``REFPROP.zip`` is placed in this repo containing the folders ``MIXTURES``, ``FLUIDS``, and ``FORTRAN`` 

## Preparation

On windows, to get gpg via chocolatey:
```
choco install gpg4win
```
, then restart restart the shell.

## Encryption

Execute:
```
gpg --symmetric --cipher-algo AES256 REFPROP.zip
```
which generates the encrypted file ``REFPROP.zip.gpg``. Generate an uncrackable password, and store that password somewhere safe. That will be used to decrypt the source

## 