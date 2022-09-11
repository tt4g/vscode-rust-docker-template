Rust template with Visual Studio Code and Docker container.

## Setup

### Project

#### Replace project name

The following files use `rust_template` or `rust-template` in their names and
should be changed.

- [Cargo.toml](./Cargo.toml)
- [docker-compose.yml](./docker-compose.yml)
- [.devcontainer/devcontainer.json](./.devcontainer/devcontainer.json)
- [.devcontainer/docker-compose.yml](./.devcontainer/docker-compose.yml)
- [.vscode/launch.json](./.vscode/launch.json)


### Rust

#### .gitignore

Remove `Cargo.lock` from [.gitignore](./.gitignore) if project will build library.

For projects that build executables, commit `Cargo.lock` to git for ABI compatibility.

#### tests

Remove dummy test files.

- [./tests/rust_template_test.rs](./tests/rust_template_test.rs)

### Docker

The `docker` directory is managed in the following structure.

```
docker
├── <image-1>
│   ├── image   Save the `Dockerfile` and any files the image needs here.
│   └── data   (Optional) Here is the file to mount in the Docker container.
├── <image-2>
│   ├── image 
│   └── data
```
