# General guidelines
- This repo will use barebone Kubernetes setup (can consider dapr for another repo/in the future)

# Architecture

- Physical architecture:
    - `_etc`: misc files (README, Build props, etc)
    - `core`: where setup codes/common infrastructure will lie (DDD entity setup, ef setup, mediatr setups, etc.)
      - `domain`: setup for DDD, mediatr, domain pipeline behaviour
      - `infrastructure`: setup for common cross-cutting concerns (auth, versioning, data access, etc)
    - `src`: contains mostly business logic(.NET), use setup code from core
      - `contracts`: common contracts between services
      - `location`: location microservice
      - `profile`: user profile microservice
      - `identity-provider`: identity provider
      - `api-gateway`: api gateway
- Logical architecture: TODO
# Technologies

## FOSS:
- **Monorepo tool**: Nx (consider merging FE to this repo?)
- **API gateway**: Kong (db-less)/Ocelot
- **Identity provider**: Keycloak/IdentityServer
- **.NET apis**:
  - locationapi
  - profileapi
- **.NET technologies**
  - Mediatr/[Mediator](https://github.com/martinothamar/Mediator#3-usage-and-abstractions)
  - EntityFramework
  - AutoMapper/Mapperly
  - Serilog
- **Fulltext search**: ElasticSearch
- **Deployment:**
  - Github Actions
  - Docker
  - Kubernetes
  - Helm
  - Linux
- **Code quality**: SonarQube/Snyk
- **Map**: google map

## External services:
- Planetscale for MySQL database with geospatial extension
- Deployment target: TODO