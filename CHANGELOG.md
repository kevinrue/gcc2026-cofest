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


Install it

```
git clone git@github.com:lh3/minibwa.git
cd minibwa
make
```

Test it

```
./minibwa
```

Export the help pages and concatenate them into a single file

```
./minibwa --help > ../minibwa-help-pages.txt 2>&1
./minibwa index --help >> ../minibwa-help-pages.txt 2>&1
./minibwa map --help >> ../minibwa-help-pages.txt 2>&1
./minibwa mem --help >> ../minibwa-help-pages.txt 2>&1
./minibwa version >> ../minibwa-help-pages.txt 2>&1
```

Get out of the minibwa directory (should have done that earlier) and run the Galaxy toolsmith:

```bash
cd ..
gtsm generate-wrapper \
  --tool-name minibwa \
  --help-text-file minibwa/minibwa-help-pages.txt \
  --provider ollama \
  --model gtsm-tools-iuc-qwen25-7b-q4 \
  --output minibwa.xml
```

```
RuntimeError: Ollama request failed for http://127.0.0.1:11434/api/generate: [Errno 61] Connection refused. Ensure Ollama is running and reachable, or set GTSM_OLLAMA_BASE_URL to the correct server.
```

Install Ollama from <https://ollama.com/>

Open web browser at <127.0.0.1:11434>. The page says "Ollama is running".

Again:

```bash
gtsm generate-wrapper \
  --tool-name minibwa \
  --help-text-file minibwa/minibwa-help-pages.txt \
  --provider ollama \
  --model gtsm-tools-iuc-qwen25-7b-q4 \
  --output minibwa.xml
```

```
RuntimeError: Ollama request failed HTTP 404: {"error":"model 'gtsm-tools-iuc-qwen25-7b-q4' not found"}
```

Following Claude's advice:

```
ollama pull qwen2.5-coder:7b
gtsm generate-wrapper \
  --tool-name minibwa \
  --help-text-file minibwa/minibwa-help-pages.txt \
  --provider ollama \
  --model qwen2.5-coder:7b \
  --output minibwa.xml
```