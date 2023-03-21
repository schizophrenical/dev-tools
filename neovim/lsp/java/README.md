# Neovim JAVA LSP Helper Script

## Introduction
Alright! You have a working Eclipse JDT LS with your neovim config. You probably updated it a couple of times too.

This helper script does the following:
- Check the configuration file to know the ff.:
  - Check if there is a configuration file in the default path. Create one if none.
  - Check the config file for directories/paths.
    - What repositories are needed to be built.
    - Where to place the built binaries.
- `git clone`s the needed repositories. _See repositories section_.
- Runs the necessary build steps (mostly `mvn clean verify`)
- Moves the needed build artifacts to the configured directories.
- Creates a reference file that lists the directories to be checked when an update is requested.
## Usage
```
USAGE: lspj [-f] [-h] [-t] [-o output_path]
            [-u]
            [-l]
            [-c hash]
            [-r hash]
            [-b config_path]
            [-h]

BUILDING:
       -u, --update         Updates and builds the repositories.
                            Uses the repositories and paths declared in the config file.
       -f, --fresh          Fresh setup. Clones and builds the repositories.
                            Uses the repositories and paths declared in the config file.
       -h, --head           Build from latest commit. Use this instead if you don't like the
                            default strategy of building from the latest tag.

OUTPUT:
       -o, --out            [Optional] Output path. Overrides the output directory path
                            declared in the config file.
       -t, --tree           [Optional] Separate the Java lsp/debug/test/decompiler files to
                            their own sub-directories.

ROLLBACK/SWITCHING:
       -l, --list           List previously built binary packages hashes.
       -c, --checkout       Switch to binary packages with the provided hash.
       -r, --rollback       Rollback to the binaries with the provided hash.
                            Defaults to the last buit binaries if no hash provided.

MISC:
       -b, --build-conf     Build a config file. Builds a copy of the default config file then
                            places it to the specified path.
                            Creates the directory tree if needed.
       -h, --help           Display usage documentation.
```

## Repositories (projects) used.
## Test
