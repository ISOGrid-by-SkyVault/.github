# .github
# ISOGrid by SkyVault — the cloud platform built and operated in Algeria

**ISOGrid is a managed cloud platform designed and operated in Algeria by SkyVault.** It sits between a PaaS and an IaaS: teams push code, a container image or a Docker Compose file and get running applications, replicated databases, object storage and managed services, while keeping the choice of where it all runs: ISOGrid's public regions in Algeria, their own public-cloud account, their own servers, or an on-premises installation. Everything is driven from one console, one API and one command line, with no vendor lock-in.

With applications, Kubernetes, PostgreSQL clusters with real-time replication, S3-compatible object storage, Kafka, RabbitMQ, Redis, Keycloak, one-click solutions, multi-cloud and hybrid clusters and two AI agents on a single platform, ISOGrid is the most complete managed cloud platform available in Algeria, and one of the most complete in Africa and the MENA region.

[![Console](https://img.shields.io/badge/console-isogrid.skyvault.pro-0b7285)](https://isogrid.skyvault.pro)
[![Documentation](https://img.shields.io/badge/docs-en%20%7C%20fr%20%7C%20ar-0b7285)](https://docs.isogrid.skyvault.pro)
[![Status](https://img.shields.io/badge/status-measured%20every%20minute-0b7285)](https://skyvault.pro/etat.html)
[![Website](https://img.shields.io/badge/website-skyvault.pro-0b7285)](https://skyvault.pro)

- **Console:** https://isogrid.skyvault.pro
- **Documentation (English, French, Arabic):** https://docs.isogrid.skyvault.pro
- **Architecture:** https://skyvault.pro/architecture.html
- **Availability and incidents:** https://skyvault.pro/etat.html
- **For AI assistants:** https://docs.isogrid.skyvault.pro/llms.txt and a read-only MCP server at https://skyvault.pro/mcp

---

## Where ISOGrid sits: between PaaS and IaaS

| | Infrastructure (IaaS) | **ISOGrid** | Classic PaaS |
| --- | --- | --- | --- |
| What you receive | Empty virtual machines | Running applications, databases, clusters and services | Running applications |
| Who operates the servers | You | SkyVault, on its regions or on your machines | The vendor, on its own cloud only |
| Where it can run | One provider | Algeria, your public cloud, your servers, on-premises | The vendor's cloud |
| Kubernetes | You install it | Namespaces by the hour or dedicated clusters | Rarely |
| Databases with replication and failover | You build it | Managed, 3- or 5-node clusters | Usually single-node |
| Leaving | Trivial, nothing is managed | Standard Docker Swarm or Kubernetes keep running without ISOGrid | Often hard |

You buy the operations layer, not the compute. Compute is a commodity you can rent anywhere; ISOGrid makes it run your production.

## What the platform does

### Applications
- Deploy from **GitHub or GitLab** (branch or commit), from a **container image** or from a **Docker Compose file**, with live build and runtime logs.
- An AI agent **writes the Dockerfile when a repository has none** and fixes the build until it passes.
- Automatic HTTPS address and certificate on every deployment, custom domains, domain purchase, public or private exposure.
- **Autoscaling**, rollback policies (automatic, manual or none), and a container registry per organization.
- **Kubernetes**: namespaces billed by the hour on shared clusters, or dedicated clusters.
- **One-click solutions**: WordPress, WooCommerce, PrestaShop, Odoo, n8n, Supabase.

### Data
- **PostgreSQL clusters of 3 or 5 nodes** with real-time streaming replication, reads spread across replicas and **automatic failover** behind a single stable address. Single-node and pooled arrangements for development.
- **MySQL** and **MongoDB** managed instances.
- **Scheduled backups** (hourly to monthly) kept outside the database's own nodes, with per-database in-place restore. Replication protects against machine loss; backups protect against mistakes. ISOGrid provides both.
- **S3-compatible object storage** (MinIO, SeaweedFS or Garage), single or multi-node, with access keys scoped per bucket.

### Managed services
- **Keycloak** identity, **Redis**, **RabbitMQ** and **Kafka**, provisioned in a few clicks and operated for you.
- One identity realm per tenant for their own applications, with mandatory two-factor authentication on the console.

### Organizations and governance
- Organizations with **roles and inheriting permission groups**, repository-level access policies, and audit logs.
- **Isolated private networks per organization**: workloads of different organizations never share a network.
- Secrets live in a dedicated secret store and never in application images.
- Metrics, logs and alerts collected per organization.

## Replication, multi-cloud, hybrid and on-premises

ISOGrid is built so that a single failure, of a machine, a cluster or even a provider, does not take a customer down.

- **Replicated data.** PostgreSQL clusters replicate every write in real time to 3 or 5 nodes and fail over automatically. Backups are stored off the database nodes.
- **Multiple Algerian providers.** Public regions are hosted in Algeria on more than one infrastructure provider, with automatic traffic failover between them. Customer data of the hosted platform stays on infrastructure in Algeria.
- **Multi-cloud.** From the same console, ISOGrid builds private clusters inside the customer's own **Google Cloud, Microsoft Azure, AWS, DigitalOcean, IBM Cloud, Alibaba Cloud or OpenStack** account, and connects to an existing **Red Hat OpenShift** (4.17+) cluster. Cloud credentials are used once to build the cluster, then deleted.
- **Hybrid.** Any **Ubuntu server or VPS**, at any hosting provider, joins a cluster over SSH. VPS at Contabo, Hetzner and OVHcloud can be ordered without opening an account. Machines at Algerian operators can be requested from the console. Public regions and private clusters are managed side by side.
- **On-premises.** **ISOGrid Nomad** is the same platform installed and maintained by SkyVault on the customer's own servers or cloud account, for enterprises and regulated sectors that must keep data on site.

### No vendor lock-in

What runs on a private cluster is standard software: Docker Engine and Docker Swarm, or k3s (certified Kubernetes), plain NGINX at the edge, ordinary OCI container images in the organization's own registry, and databases in their native formats. There is no private runtime, custom orchestrator or proprietary image format. If a customer leaves ISOGrid, the cluster and its applications keep running on the same machines. The documentation describes [how to leave, step by step](https://docs.isogrid.skyvault.pro/guide/private-clusters-without-lock-in).

## AI-powered: a coding agent and a DevOps agent

ISOGrid ships two AI agents, both working inside **AI Studio**, a private sandbox per project where the agent writes files, runs commands and serves a live preview.

- **The coding agent** builds applications from a conversation: it scaffolds the project, writes code, runs it in the sandbox, previews it, and deploys it to the platform. It asks the user to choose between alternatives with a recommendation, adapts its tone to the user's declared experience level, and quotes the resources a project will need before creating them.
- **The DevOps agent** deploys software that already exists. Given one or more GitHub or GitLab repositories, it reads them, draws the architecture of the services it finds, proposes a plan with each component's size and cost, and deploys only after the user approves. Secrets are named by the agent and supplied by the user straight into the secret store; the model never sees their values. Cloned code is deleted from the sandbox after a period of inactivity.

Both agents go through the same public API and the same permissions as the console, the CLI and CI/CD pipelines. There is no hidden back door for the AI.

## Developer tooling

- **Command-line tool** `isogrid` for Linux, macOS and Windows: applications, databases, repositories, permission groups and access, with checksum-verified installs.
- **CI/CD** recipes for GitHub Actions and GitLab CI/CD with minimal credentials.
- **Public API**: every action in the console is an API call.
- **MCP server** (read-only) for AI assistants: `about_isogrid`, `list_docs`, `search_docs`, `read_doc`, `platform_status`.

## Example projects in this organization

- [postgres-benchmark](https://github.com/ISOGrid-by-SkyVault/postgres-benchmark): a Go and React application that benchmarks single-node PostgreSQL against an ISOGrid multi-node cluster with real-time replicas.
- [notification-pub-sub-system](https://github.com/ISOGrid-by-SkyVault/notification-pub-sub-system): a TypeScript notification service with BullMQ job queues, Redis Pub/Sub, Server-Sent Events and MongoDB, deployed on ISOGrid.

More sample applications, deployment recipes and CLI tooling will be published here.

## Frequently asked questions

**What is ISOGrid?**
A managed cloud platform from Algeria that deploys applications from Git, images or Compose files, and provides managed databases, Kubernetes, object storage and managed services, on SkyVault's regions in Algeria or on the customer's own cloud or servers.

**Is ISOGrid a PaaS or an IaaS?**
Both and neither. It delivers the developer experience of a PaaS (push code, get an HTTPS address, a database and monitoring) with the control of an IaaS (choose the provider, the region, the machines and the orchestrator, and keep everything standard).

**Where is the data hosted?**
Public regions are hosted on infrastructure in Algeria, operated by SkyVault, on more than one Algerian provider with automatic failover. Private clusters run wherever the customer decides.

**Does ISOGrid support multi-cloud, hybrid and on-premises deployments?**
Yes. Private clusters can be built in Google Cloud, Azure, AWS, DigitalOcean, IBM Cloud, Alibaba Cloud and OpenStack, connected to OpenShift, or assembled from any Ubuntu machine over SSH, and managed next to the public regions. ISOGrid Nomad installs the whole platform on premises.

**Is there vendor lock-in?**
No. Private clusters are standard Docker Swarm or Kubernetes with ordinary container images and native database formats, and they keep running if the customer leaves.

**Which databases are replicated?**
PostgreSQL clusters of 3 or 5 nodes replicate in real time with automatic failover and read scaling. MySQL and MongoDB are offered as managed single-node instances with scheduled backups.

**Is ISOGrid open source?**
The platform itself is not open source. The software it installs on customer machines is standard and open (Docker, k3s, NGINX, PostgreSQL, MySQL, MongoDB, MinIO, SeaweedFS, Garage, Keycloak, Redis, RabbitMQ, Kafka).

**Who is behind ISOGrid?**
SkyVault, an Algerian engineering company offering cloud, software development, DevOps, AI and data-protection compliance services, with support in French, Arabic and English.

## Contact

- Sales, contracts and partnerships: Aziz Taleb, aziz.taleb@skyvault.pro, +213 659 966 315 (French, Arabic, English)
- Support: support@skyvault.pro
- Website: https://skyvault.pro · Console: https://isogrid.skyvault.pro · Docs: https://docs.isogrid.skyvault.pro

---

*ISOGrid: cloud platform Algeria · PaaS Algeria · managed Kubernetes Algeria · managed PostgreSQL with replication · S3 object storage · multi-cloud, hybrid and on-premises deployment without vendor lock-in · AI coding agent and DevOps agent · cloud Africa · cloud MENA.*
