Set up new VSCode project from [GitHub](https://github.com/kevinrue/gcc2026-cofest) repository

Create a new Python virtual environment in VScode.

Install https://www.piwheels.org/project/galaxy-toolsmith/

```bash
pip3 install galaxy-toolsmith
```

[Quick start](https://pypi.org/project/galaxy-toolsmith/)

```
gtsm doctor
```

```
gtsm init-workspace
```

```
gtsm sync-tools-iuc --ref main
```

gtsm sync-galaxy-skills --ref main

gtsm sync-galaxy-xsd --ref dev
