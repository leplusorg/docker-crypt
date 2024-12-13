# Cipher/deciper/sign

Docker container to cipher/decipher/sign data (gnupg, openssl...).

[![Dockerfile](https://img.shields.io/badge/GitHub-Dockerfile-blue)](https://github.com/leplusorg/docker-crypt/blob/main/crypt/Dockerfile)
[![Docker Build](https://github.com/leplusorg/docker-crypt/workflows/Docker/badge.svg)](https://github.com/leplusorg/docker-crypt/actions?query=workflow:"Docker")
[![Docker Stars](https://img.shields.io/docker/stars/leplusorg/crypt)](https://hub.docker.com/r/leplusorg/crypt)
[![Docker Pulls](https://img.shields.io/docker/pulls/leplusorg/crypt)](https://hub.docker.com/r/leplusorg/crypt)
[![Docker Version](https://img.shields.io/docker/v/leplusorg/crypt?sort=semver)](https://hub.docker.com/r/leplusorg/crypt)

## Example without using the filesystem

Let's say that you have a file `foo.txt` in your current working directory that you want to encrypt with a public key `age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7`:

**Mac/Linux**

```bash
cat foo.txt | docker run --rm -i --net=none leplusorg/crypt age --recipient age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7 > foo.age
```

**Windows**

```batch
type foo.txt | docker run --rm -i --net=none leplusorg/crypt age --recipient age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7 > foo.age
```

## Example using the filesystem

Same thing, assuming that you have a file `foo.txt` in your current working directory that you want to encrypt with a public key `age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7`:

**Mac/Linux**

```bash
docker run --rm -t --user="$(id -u):$(id -g)" --net=none -v "$(pwd):/tmp" leplusorg/crypt age --recipient age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7 --output /tmp/foo.age /tmp/foo.txt
```

**Windows**

In `cmd`:

```batch
docker run --rm -t --net=none -v "%cd%:/tmp" leplusorg/crypt age --recipient age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7 --output /tmp/foo.age /tmp/foo.txt
```

In PowerShell:

```pwsh
docker run --rm -t --net=none -v "${PWD}:/tmp" leplusorg/crypt age --recipient age1u9wu5f2eajlqluhra0jx6qxjeyyr2jygh6vguacrp9pd63kljsesam7cg7 --output /tmp/foo.age /tmp/foo.txt
```

## Request new tool

Please use [this link](https://github.com/leplusorg/docker-crypt/issues/new?assignees=thomasleplus&labels=enhancement&template=feature_request.md&title=%5BFEAT%5D) (GitHub account required) to request that a new tool be added to the image. I am always interested in adding new capabilities to these images.
