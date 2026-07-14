# podcast-genarator

A small utility to generate and update a podcast RSS feed from local metadata or audio files.

## Features

- Generates an RSS feed via `feed.py`.
- Intended to be run in CI (GitHub Actions) using `entrypoint.sh` and the included `Dockerfile`.

## Requirements

- Python 3.8+ (or `python` / `python3` available in PATH)
- Git (for committing and pushing updates when used in CI)

## Quick start

Run the feed generator locally:

```bash
python3 feed.py
```

If your environment uses `python` instead of `python3`:

```bash
python feed.py
```

## Docker

Build the image:

```bash
docker build -t podcast-generator .
```

Run the container (example):

```bash
docker run --rm -v "$(pwd)":/github/workspace -e GITHUB_ACTOR=me -e INPUT_EMAIL=me@example.com podcast-generator
```

## Entrypoint (CI)

The repository includes `entrypoint.sh` which is written to be used in GitHub Actions. It:

- configures git user and safe directory
- runs `feed.py`
- commits and pushes only if there are changes

## Development

- Edit `feed.py` to change feed generation logic.
- Use the Docker image for reproducing CI runs locally.

## License

This project is licensed under the terms in the `LICENSE` file.
