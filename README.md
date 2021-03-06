# Event Store Certificate Generation CLI

The command line interface to ease the generation of a certificate authority and node certificates for EventStoreDB 20.6.x and above.

## Getting Started

### Releases
The latest release for the es-gencert-cli can be found under the [GitHub releases page](https://github.com/EventStore/es-gencert-cli/releases).
We releases binaries for Windows, Linux and macOS. We also publish the tool as a Docker image.

### Usage

Basic usage for es-gencert-cli:
```
./es-gencert-cli [options] <command> [args]
```

Getting help for a specific command:

```bash
./es-gencert-cli -help <command>
```
e.g.

```bash
./es-gencert-cli -help create-ca

Usage: create_ca [options]
  Generate a root/CA TLS certificate to be used with EventStoreDB
Options:
  -days                       The validity period of the certificate in days (default: 5 years)
  -out                        The output directory (default: ./ca)
```

## Running with Docker

You could also run the tool using Docker interactive container:

```bash
docker run --rm -i eventstore/es-gencert-cli <command> <options>
```

One useful scenario is to use the tool inside the Docker Compose file to generate all the necessary certificates before starting cluster nodes. You can find an [example](https://github.com/EventStore/EventStore/blob/master/docker-compose.yml) in the EventStoreDB repository.

### Examples

Generating a certificate authority:

```bash
./es-gencert-cli create-ca -out ./es-ca
```

Generating a certificate for an EventStoreDB node:

```
./es-gencert-cli-cli create-node -ca-certificate ./es-ca/ca.crt -ca-key ./es-ca/ca.key -out ./node1 -ip-addresses 127.0.0.1,172.20.240.1 -dns-names localhost,eventstore-node1.localhost.com
```

## Development

Building or working on `es-gencert-cli` requires a Go environment, version 1.14 or higher.
