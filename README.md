# Firefox Secure Policies
These policies provide a minimal hardening to Firefox's configuration.

NOTE: These policies have only been tested on Debian. Furthermore, some policies may only be compatible with `firefox-esr`.

Read more about Firefox policies [here](https://github.com/mozilla/policy-templates).

## Installation
```
$ git clone https://github.com/andrea-varesio/firefox-secure-policies
```

### Debian:
```
$ sudo mkdir -p /usr/lib/firefox-esr/distribution
$ cat firefox-secure-policies/policies.json | sudo tee /usr/lib/firefox-esr/distribution/policies.json &> /dev/null
```

### Fedora:
```
$ sudo mkdir -p /usr/lib64/firefox/distribution
$ cat firefox-secure-policies/policies.json | sudo tee /usr/lib64/firefox/distribution/policies.json &> /dev/null
```

## Troubleshooting
**Q:** **The policies are not working.**<br />
**A:** You may need to remove existing profiles (**WARNING: this may lead to loss of data!**):
```
$ rm -rf $HOME/.mozilla
```

**Q:** **Can't access `about:debugging`.**<br />
**A:** Remove the following policy or change its value to `allowed`:
```
"*": {
    "installation_mode": "blocked"
}
```
**Q:** **Can't install additional addons.**<br />
**A:** Add an exception for your desired addon in `"ExtensionSettings"` or follow the suggestion for the question above.

**Q:** **How to change the default search engine.**<br />
**A:** Find the `"SearchEngines"` policy and edit `"Default": "StartPage"` accordingly.

**Q:** **How to disable automatic installation of addons.**<br />
**A:** Find the `"ExtensionSettings"` policy and change the value of `"installation_mode"` from `"normal_installed"` to `"allowed"`.

**Q:** **Some search engines are not removed.**<br />
**A:** Find the `"SearchEngines"` policy and add a TLD to the faulty search engine (for example: change `"Amazon"` to `"Amazon.com"`).

## LICENSE
Mozilla Public License Version 2.0

Copyright (C) 2022-2023 Andrea Varesio <https://www.andreavaresio.com>