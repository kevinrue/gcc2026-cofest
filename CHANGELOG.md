Set up new VSCode project from [GitHub](https://github.com/kevinrue/gcc2026-cofest) repository

Create a new Python virtual environment in VScode.

Install https://www.piwheels.org/project/galaxy-toolsmith/

```bash
pip3 install galaxy-toolsmith
```

Follow the [Quick start](https://pypi.org/project/galaxy-toolsmith/) instructions.

```bash
gtsm doctor
```

```bash
gtsm init-workspace
```

```bash
gtsm sync-tools-iuc --ref main
```

```bash
gtsm sync-galaxy-skills --ref main
```

```bash
gtsm sync-galaxy-xsd --ref dev
```

```bash
gtsm extract-corpus --max-workers 8
```

```bash
gtsm list-train-profiles
```

Skip over model training steps

Pick a tool that isn't in Galaxy yet, e.g. [minibwa](https://github.com/lh3/minibwa)

Activate my conda environment

```bash
miniforge_activate_base
```

Install it using Conda

