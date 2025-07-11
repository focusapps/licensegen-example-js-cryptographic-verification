# Example Cryptographic Verification
This is an example of cryptographically validating license keys, and
extracting embedded tamper-proof data within the key for offline use, all
with your LicenseGen account's public key. You can find your public key within
[your account's settings page](https://licensegen-admin.focusapps.app/settings).

Cryptographically validating encrypted and signed licenses can be used
to implement offline licensing, as well as adding additional security to
your licensing model. All that is needed to cryptographically validate
a license is your account's public key.

The license's policy _must_ implement one of the following [schemes](https://licensegen.focusapps.app/docs/api/#policies-create-attrs-scheme):

- `ED25519_SIGN`
- `RSA_2048_PKCS1_SIGN_V2`
- `RSA_2048_PKCS1_PSS_SIGN_V2`
- `RSA_2048_PKCS1_ENCRYPT`
- `RSA_2048_JWT_RS256`

## Running the example

First up, add an environment variable containing your public key:

```bash
# Your LicenseGen account's Ed25519 or RSA public key
export LICENSEGEN_PUBLIC_KEY="YOUR_PUBLIC_KEY_HERE"
```

You can either run each line above within your terminal session before
starting the app, or you can add the above contents to your `~/.bashrc`
file and then run `source ~/.bashrc` after saving the file.

Next, install dependencies with [`yarn`](https://yarnpkg.comg):

```
yarn
```

Then run the script, passing in the `key` as well as the `scheme`:

```
yarn start --scheme ED25519_SIGN --key SOME_SIGNED_LICENSE_KEY_HERE

# or...
yarn start -s RSA_2048_PKCS1_PSS_SIGN_V2 -k SOME_LICENSE_KEY_HERE
```

How a given license key is validated will depend on the scheme. Please
review the code for a more thorough overview of how each scheme is
validated. Be sure to copy your public key correctly - your keys will
fail validation if it is copied incorrectly. You can find your public
key in [your account's settings](https://licensegen-admin.focusapps.app/settings).

## Questions?

Reach out at [licensegen@focusapps.app](mailto:licensegen@focusapps.app) if you have any
questions or concerns!
