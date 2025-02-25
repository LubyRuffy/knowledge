# Knowledge

Standalone Knowledge Tool to be used with GPTScript and GPTStudio.

## Background

- Embedded SQLite as File Index
- Embedded VectorDB as Embeddings Storage

## Build

Requires Go 1.22+

```bash
make build
```

## Run

The knowledge tool can run in two modes: server and client, where client can be standalone or referring to a remote server.


### Client - Standalone

#### Default Dataset

```bash
knowledge list-datasets
```

```bash
knowledge get-dataset default
```

```bash
knowledge ingest README.md
```

```bash
knowledge get-dataset default
```

```bash
knowledge retrieve "Which filetypes are supported?"
```

#### Custom Dataset

```bash
knowledge create-dataset foobar
knowledge ingest -d foobar README.md
knowledge retrieve -d foobar "Which filetypes are supported?"
knowledge delete-dataset foobar
```

### Server & Client - Server Mode

```bash
knowledge server
```

```bash
export KNOW_SERVER_URL=http://localhost:8000/v1
knowledge create-dataset foobar
knowledge ingest -d foobar README.md
knowledge retrieve -d foobar "Which filetypes are supported?"
knowledge delete-dataset foobar
```

## Supported File Types

- `.pdf`
- `.html`
- `.md`
- `.txt`
- `.docx`
- `.odt`
- `.rtf`
- `.csv`
- `.ipynb`
- `.json`

## OpenAPI / Swagger

The API is documented using OpenAPI 2.0 (Swagger), automatically generated using [`swaggo/swag`](https://github.com/swaggo/swag) (`make openapi`).

## GPTScript Examples

Note: The examples in the `examples/` directory expect the `knowledge` binary to be in your `$PATH`.

### Run

```bash
gptscript examples/client.gpt
```
