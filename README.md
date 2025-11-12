<!--
SPDX-License-Identifier: Apache-2.0
Copyright 2022-present Open Networking Foundation
-->

[![Go Report Card](https://goreportcard.com/badge/github.com/omec-project/sctplb)](https://goreportcard.com/report/github.com/omec-project/sctplb)

# sctplb

Compliance of the 5G Network Functions can be found at [5G Compliance](https://docs.sd-core.opennetworking.org/main/overview/3gpp-compliance-5g.html)

## Repository Structure

Below is a high-level view of the repository and its main components:
```
.
├── backend                     # Contains the core logic for the SCTP Load Balancer, including gRPC service implementation, scheduling algorithms, and type definitions.
│   ├── grpc.go
│   ├── sched.go
│   ├── sched_test.go
│   ├── service.go
│   └── type.go
├── client.proto
├── config                      # Holds configuration-related code and files, such as the main runtime configuration (sctplb.yaml) and test configurations.
│   ├── config.go
│   ├── config_test.go
│   └── sctplb.yaml
├── context                     # Defines shared runtime contexts used across the application for managing state and process control.
│   └── context.go
├── Dockerfile
├── Dockerfile.fast
├── go.mod
├── go.mod.license
├── go.sum
├── go.sum.license
├── LICENSES
│   └── Apache-2.0.txt
├── logger                      # Implements the logging utility for system-wide message and event logging.
│   └── logger.go
├── Makefile                    # Includes build, test, and deployment automation commands.
├── README.md
├── sctplb.go                   # Main entry point for running the SCTP Load Balancer service.
├── sdcoreAmfServer             # Contains generated gRPC client code (.pb.go files) used for communication between the SCTPLB and other 5G Core services (e.g., AMF).
│   ├── client_grpc.pb.go
│   └── client.pb.go
├── Taskfile.yml                # Includes build, test, and deployment automation commands.
├── test-mirror.txt
├── VERSION
└── VERSION.license

7 directories, 27 files
```


## Configuration and Deployment

**Docker**

To build the container image:
```
task mod-start
task build
task docker-build-fast
```

**Kubernetes**

The standard deployment uses Helm charts from the Aether project. The version of the Chart can be found in the OnRamp repository in the `vars/main.yml` file.


## Quick Navigation

| Type                | File / Directory                                                           | Description                                                        |
| ------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| Core Service     | [`sctplb.go`](./sctplb.go)                                                 | Main entry point for the SCTP Load Balancer service.               |
| Configuration    | [`config/sctplb.yaml`](./config/sctplb.yaml)                               | Defines runtime parameters for the load balancer.                  |
| Backend Logic    | [`backend/`](./backend)                                                    | Contains the scheduling logic and gRPC service implementations.    |
| Context          | [`context/context.go`](./context/context.go)                               | Defines shared runtime context and operational state handling.     |
| gRPC Interface   | [`client.proto`](./client.proto) / [`sdcoreAmfServer/`](./sdcoreAmfServer) | Protocol Buffers and generated client code for gRPC communication. |
| Logging          | [`logger/logger.go`](./logger/logger.go)                                   | Implements centralized logging utilities.                          |
| Containerization | [`Dockerfile`](./Dockerfile) / [`Dockerfile.fast`](./Dockerfile.fast)      | Standard and optimized container build definitions.                |
| Build Tools      | [`Makefile`](./Makefile) / [`Taskfile.yml`](./Taskfile.yml)                | Build, test, and automation configurations.                        |
| Dependencies     | [`go.mod`](./go.mod) / [`go.sum`](./go.sum)                                | Go dependency management files.                                    |
| License          | [`LICENSES/Apache-2.0.txt`](./LICENSES/Apache-2.0.txt)                     | Apache 2.0 license file for open-source compliance.                |
| Version          | [`VERSION`](./VERSION)                                                     | Defines the component version.                                     |
| Documentation    | [`README.md`](./README.md)                                                 | Repository-level documentation and usage guide.                    |


## Reach out to us thorugh

1. #sdcore-dev channel in [ONF Community Slack](https://onf-community.slack.com/)
2. Raise Github issues
