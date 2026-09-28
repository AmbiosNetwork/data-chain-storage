# Data Chain Storage

Data Chain Storage is an open-source environmental-data toolkit from Ambient Technologies Inc., operating as Ambios Network. It is designed to prepare, sanitize, package, version, store, retrieve, and verify approved environmental dataset releases.

The project combines:

- **Solana** for public verification of manifest integrity, version, timestamp, and publisher reference.
- **Filecoin** for decentralized storage, retrieval, and checksum verification of approved off-chain dataset packages.

Raw environmental observations remain off-chain.

## Repository Status

This repository currently establishes the project's public scope, architecture, licensing, roadmap, and public/private boundaries.

The complete implementation is not yet published. Grant-funded public code, tests, schemas, examples, and documentation will be added through the planned development milestones after private material has been removed and the public components have been reviewed, tested, commented, and documented.

An internal Solana registry/index contract has been developed and will be evaluated alongside the simpler signed-transaction approach before the final public implementation is selected.

## Project Goals

The toolkit will help developers and data publishers:

1. Create deterministic manifests for approved environmental dataset releases.
2. Record dataset rights, limitations, versions, timestamps, and publisher references.
3. Package and compress approved data for off-chain storage.
4. Store and retrieve packages through supported Filecoin workflows.
5. Register compact manifest references through Solana.
6. Verify that a retrieved package or manifest matches its published reference.
7. Track relationships between previous and superseding dataset versions.

## High-Level Workflow

### 1. Approved Data Input

The toolkit begins with an approved public or sanitized dataset export. Commercial, partner-restricted, personal, precise-location, and internal infrastructure data are excluded unless their use and release have been expressly authorized.

### 2. Sanitization and Rights Controls

The workflow applies rights-aware restrictions covering privacy, commercial terms, partner requirements, location generalization, and permitted use.

### 3. Packaging and Manifest Generation

The toolkit creates a deterministic, machine-readable manifest containing items such as:

- Dataset identity
- Generalized geography
- Monitoring period
- Environmental fields
- Version and previous-version references
- Rights and use limitations
- File inventory
- Retrieval reference
- Publisher information

Cryptographic hashes, checksums, and content identifiers are generated for integrity verification.

### 4. Solana Manifest Verification

The planned Solana implementation has two possible paths:

- **Phase 1:** A signed publisher transaction records the manifest hash, version, timestamp, publisher reference, and approved retrieval reference.
- **Phase 2:** A lightweight versioned registry/index may be used when it provides a clearer and more maintainable lookup workflow.

The final approach will be selected based on security, maintainability, cost, and developer usability.

### 5. Filecoin Storage and Retrieval

Approved dataset packages can be prepared using Parquet with embedded Snappy compression followed by Brotli. The Filecoin workflow will support:

- Package creation
- Manifest creation
- Storage onboarding
- Content identifier recording
- Retrieval at defined checkpoints
- Checksum verification
- Version and storage-status tracking

### 6. Verification and Version Lineage

A verifier recalculates the relevant hash or checksum, checks the Solana reference or Filecoin package record, and returns a structured result. New manifest versions can reference previous or superseded releases.

## Verification Boundary

The toolkit verifies digital integrity and publication references. It can verify manifest integrity, version, timestamp, publisher reference, retrieval reference, and checksum agreement.

It does **not** verify or certify:

- Sensor accuracy
- Sensor calibration
- Scientific validity
- Regulatory suitability
- Legal compliance of a dataset
- Medical or health interpretation
- Fitness for a particular operational decision

Users remain responsible for assessing the underlying data, rights, scientific limitations, and intended use.

## Planned Public Components

The public repository may include:

- Data and package schemas
- Manifest schema and generator
- Deterministic canonicalization and hashing functions
- Sanitized or synthetic sample data
- Filecoin packaging, upload, retrieval, and checksum workflows
- Solana signed-transaction registration and verification workflows
- A registry/index reference implementation if selected
- Command-line and reference-library tooling
- Automated tests and sanitized test fixtures
- Setup and integration instructions
- Architecture and security documentation
- Responsible-use guidance
- Grant-related public-good examples

## Excluded Private Components

The public repository will not include:

- Proprietary Ambios platform code
- Commercial, personal, partner-restricted, or otherwise protected datasets
- Credentials, secrets, private keys, or tokens
- Private endpoints or internal service addresses
- Elasticsearch queries or index details
- Internal infrastructure and deployment configuration
- Partner-controlled materials without permission
- Any code that has not completed the required public/private separation and security review

The public toolkit will begin with an already approved package or a generic data-source interface. Access to Ambios private infrastructure is not required to use the public components.

## Development Roadmap

### Repository Foundation

- Publish project scope and architecture
- Publish approved licence files
- Document public/private boundaries
- Document development and release milestones

### Public Beta

- Release manifest schema, generator, and validation rules
- Release sanitized examples and test fixtures
- Release Solana registration and verification workflow
- Release Filecoin packaging, retrieval, and checksum workflow
- Complete unit, integration, negative, versioning, and security tests

### Versioning and Developer Release

- Finalize the signed-transaction or registry/index approach
- Publish version-lineage support
- Add command-line and reference-library examples
- Complete documentation, dependency, secret, and repository-history reviews
- Publish the beta release

### Maintenance and Adoption

- Provide six months of active maintenance after public beta
- Triage issues and publish maintenance updates
- Support external workflow testing and integrations
- Publish demonstration and adoption materials

## Security and Responsible Publication

Do not commit credentials, private endpoints, Elasticsearch queries, restricted data, or internal infrastructure details. Every public release should complete a secrets scan, dependency review, licence review, test run, and repository-history review.

Security concerns should be reported privately to Ambios Network before public disclosure.

## Licensing

- **Source code and technical examples:** [Apache License 2.0](LICENSE)
- **Documentation, schemas, templates, and non-code materials:** [Creative Commons Attribution 4.0 International](LICENSE-DOCUMENTATION.md)
- **Datasets:** Separate rights and licence terms apply to each dataset. No dataset rights are granted merely because code or documentation is published in this repository.

Ambios proprietary infrastructure, internal systems, protected data, Elasticsearch queries, and other excluded materials remain outside these public licences.

## Organization

- **Owner:** AmbiosNetwork
- **Repository:** data-chain-storage
- **Website:** https://ambios.network/

## Disclaimer

This project is under active development. Interfaces, schemas, and implementation details may change before the first public beta. Use of the toolkit does not replace independent technical, scientific, legal, privacy, or regulatory review.
