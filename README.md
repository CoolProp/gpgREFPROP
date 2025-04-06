# Encrypted REFPROP 

Following the instructions from https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions, a zip file called ``REFPROP.zip`` is placed in this repo containing the folders ``MIXTURES``, ``FLUIDS``, and ``FORTRAN``.

## Preparation

On windows, to get gpg via chocolatey:
```
choco install gpg4win
```
, then restart restart the shell. Other platforms have ``gpg`` available by default

## Encryption

Choose your passphrase and place in the ``passphrase`` file. Perhaps auto-generated.

Execute:
```
gpg --passphrase `cat passphrase` -c --symmetric --cipher-algo AES256 --batch REFPROP.zip
```
which generates the encrypted file ``REFPROP.zip.gpg``. 

## Actions setup

Add a repository secret called ``REFPROP_GPG_PASSPHRASE`` in github actions with the contents of the password you generated in the previous step. The action in this repository will test the decryption and print out the contents of the zip file, as well as building a shared library based on the sources in the encrypted zip.