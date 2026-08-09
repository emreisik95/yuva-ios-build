# YuVa encrypted iOS build mirror

This public repository contains no plaintext application source, signing
identity, provisioning profile, passphrase, or installable IPA. It exists only
to run a manual macOS GitHub Actions build from an authenticated OpenPGP archive.

The source archive is prepared in the private `home-system` repository. The
workflow decrypts it only inside an ephemeral runner, runs the Swift and iOS test
suites, signs YuVa with GitHub Actions Secrets, encrypts the resulting IPA, and
uploads the ciphertext for one day.

Pull requests and pushes do not trigger builds. Forks do not receive repository
Secrets. A successful artifact is not installable until it is downloaded,
decrypted privately, and its signature and embedded provisioning profile are
verified.
