# unduome.github.io

[unduome.github.io](https://unduome.github.io/) serves the same files as [unduo.me](https://unduo.me/), for networks that block newly registered domains. The University of Toronto's wifi blocks unduo.me for that reason.

The source, and everything else about UnDuo, is in [UnDuoMe/unduo.me](https://github.com/UnDuoMe/unduo.me). This repository holds only the workflow that copies its site here.

## How it stays the same

Every ten minutes, [`mirror.yml`](.github/workflows/mirror.yml) checks out `www/` from unduo.me's `main` branch. When this site differs from it, the workflow downloads every file from unduo.me first, and deploys only if each one matches byte for byte, so this site serves only what unduo.me serves. `CNAME` is the one file left out. A change on unduo.me shows up here within about ten minutes, or longer when GitHub delays scheduled runs.

Because the bytes are the same, a setup file downloaded here has the same SHA-256 as one from unduo.me, and verifies the same way:

```sh
gh attestation verify "UnDuo - University of Toronto.html" --repo UnDuoMe/unduo.me
```
