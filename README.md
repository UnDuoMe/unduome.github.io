# unduome.github.io

[unduome.github.io](https://unduome.github.io/) serves the same files as [unduo.me](https://unduo.me/), for networks that block newly registered domains. The University of Toronto's wifi blocks unduo.me for that reason.

The source, and everything else about UnDuo, is in [UnDuoMe/unduo.me](https://github.com/UnDuoMe/unduo.me). This repository only hosts the copy.

## How it stays the same

Every time unduo.me deploys, the `mirror` job in its [Deploy workflow](https://github.com/UnDuoMe/unduo.me/blob/main/.github/workflows/deploy.yml) pushes the build it just published to this repository's [`site`](https://github.com/UnDuoMe/unduome.github.io/tree/site) branch, which GitHub Pages publishes. `CNAME` is the one file left out. Each commit there names the unduo.me commit and the workflow run that built it. The job then waits until this site serves the same bytes.

It pushes with a deploy key that can write only to this repository.

Because the bytes are the same, a setup file downloaded here has the same SHA-256 as one from unduo.me, and verifies the same way:

```sh
gh attestation verify "UnDuo - University of Toronto.html" --repo UnDuoMe/unduo.me
```
