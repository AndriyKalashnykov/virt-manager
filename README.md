[![CI](https://github.com/virt-manager/virt-manager/actions/workflows/ci.yml/badge.svg?branch=main)](https://github.com/virt-manager/virt-manager/actions/workflows/ci.yml)
[![Hits](https://hits.sh/github.com/virt-manager/virt-manager.svg?view=today-total&style=plastic)](https://hits.sh/github.com/virt-manager/virt-manager/)

# Virtual Machine Manager

`virt-manager` is a graphical tool for managing virtual machines
via [libvirt](https://libvirt.org). Most usage is with QEMU/KVM
virtual machines, but Xen and libvirt LXC containers are well
supported. Common operations for any libvirt driver should work.

Several command line tools are also provided:

 - `virt-install`: Create new libvirt virtual machines
 - `virt-clone`: Duplicate existing libvirt virtual machines
 - `virt-xml`: Edit existing libvirt virtual machines/manipulate libvirt XML

## Quick Start

```bash
./virt-manager --debug      # run virt-manager from git checkout
./virt-install --debug ...  # run virt-install from git checkout
```

For dependency info and installation instructions, see
[INSTALL.md](INSTALL.md).

## CI/CD

GitHub Actions runs on every push to `main` and on pull requests.

| Workflow | Triggers | Purpose |
|----------|----------|---------|
| **Test on fedora:latest** | push (main), PR | Build RPM, run pytest with coverage, upload to Codecov |
| **Check code using pre-commit** | push (main), PR, manual | Run pre-commit hooks (black, ruff, yaml checks) |
| **Scan with codespell** | PR, manual | Spell-check the codebase |
| **Test against libvirt.git** | schedule (every 3 days) | Build latest libvirt from source and run tests |
| **Translations** | schedule (every 2 days) | Regenerate .pot file and push to translations branch |
| **Cleanup old workflow runs** | schedule (weekly), manual | Delete workflow runs older than 7 days |

## Contact

 - For IRC we use #virt on OFTC.
 - For bug reporting info, see
   [virt-manager bug reporting](https://virt-manager.org/bugs).
 - There are further project details on the
   [virt-manager](https://virt-manager.org/) website.
 - See the [CONTRIBUTING.md](CONTRIBUTING.md) file for info about submitting patches or
   contributing translations.
