# Virtual Machine Manager

Graphical tool for managing virtual machines via libvirt (QEMU/KVM, Xen, LXC). Python application with GTK UI, built with meson.

## Tech Stack

- **Language**: Python 3
- **UI**: GTK 3 via PyGObject
- **Virtualization**: libvirt
- **Build System**: Meson
- **Testing**: pytest + pytest-cov
- **Linting**: ruff, black, pre-commit
- **Packaging**: RPM (spec included)

## Project Structure

```
virtManager/     # GTK application code (virt-manager GUI)
virtinst/        # CLI/library code (virt-install, virt-clone, virt-xml)
ui/              # Glade XML UI definitions
tests/           # Test suite (pytest)
man/             # Man page sources
data/            # Desktop files, icons, GSettings schemas
po/              # Translation files (.pot, .po)
scripts/         # Build and utility scripts
```

## Common Commands

```bash
./virt-manager --debug        # Run virt-manager from checkout
./virt-install --debug ...    # Run virt-install from checkout
meson setup build             # Configure build directory
meson dist -C build           # Create source distribution
pytest                        # Run test suite
pytest --cov --cov-report=xml # Run tests with coverage
```

## CI

GitHub Actions workflows (`.github/workflows/`):

| Workflow | Triggers | Steps |
|----------|----------|-------|
| **ci.yml** | push (main), PR | Install deps on fedora:latest, build RPM, pytest with coverage, Codecov upload |
| **pre-commit.yml** | push (main), PR, manual | Run pre-commit hooks (black, ruff, yaml checks) |
| **codespell.yml** | PR, manual | Spell-check the codebase |
| **test-against-libvirt-git.yml** | schedule (every 3 days) | Build latest libvirt from source, run tests with --error-for-skips |
| **translations.yml** | schedule (every 2 days) | Regenerate .pot file, push to translations branch |
| **cleanup-runs.yml** | schedule (weekly), manual | Delete workflow runs older than 7 days |

Concurrency is enabled with `cancel-in-progress: true`. Actions are pinned to commit SHAs.

## Skills

Use the following skills when working on related files:

| File(s) | Skill |
|---------|-------|
| `README.md` | `/readme` |
| `.github/workflows/*.yml` | `/ci-workflow` |

When spawning subagents, always pass conventions from the respective skill into the agent's prompt.
