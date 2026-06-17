# sh-validate-syntax

Validate JSON and YAML files from the terminal.

This is a small local utility for syntax checks. It uses file suffixes when they are available and supports explicit format flags for extensionless files.

## What it does

1. Validates JSON with `jq`
2. Validates YAML with `yq`
3. Auto-detects the format from `.json`, `.yaml`, and `.yml`
4. Supports `--json` and `--yaml` for extensionless files
5. Supports `--strict` to reject YAML input that is also valid JSON
6. Prints the parser error when validation fails

## Flags

- `--json` validates as JSON
- `--yaml` validates as YAML
- `--strict` applies only to YAML validation
- Extensionless files require an explicit format flag
- YAML accepts JSON syntax unless `--strict` is used

## Usage

From inside this repository:

```bash
./validate-syntax path-to/file.json
./validate-syntax path-to/file.yaml
./validate-syntax --yaml --strict path-to/file-yaml
./validate-syntax --json path-to/file-json
```

### Install as a command

To make `validate-syntax` available from anywhere, keep a stable copy of the script outside the working repository.

1. Copy the script to a safe location

```bash
mkdir -p ~/bin
cp ./validate-syntax ~/bin/validate-syntax
chmod +x ~/bin/validate-syntax
```

2. Make sure `~/bin` is on your `PATH`

```bash
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
```

3. Reload your shell

```bash
source ~/.bashrc
```

### Recommended workflow

- Keep the script in a stable location outside the working repository
- Update the stable copy manually when you want a new version
- Run it on files you want to validate by syntax only
