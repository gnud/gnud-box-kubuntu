# gnud-box-kubuntu
List of curated packages for Kubuntu

This repository is used to make a list of all useful things I need for Python and Node development.

# Listing packages:

```bash
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)
```
