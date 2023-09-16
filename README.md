# General guidelines
- This repo will use barebone Kubernetes setup (can consider dapr for another repo/in the future)

# Architecture

- Physical architecture:
    - `_etc`: misc files (README, Build props, etc)
    - `core`: where setup codes/common infrastructure will lie (DDD entity setup, ef setup, mediatr setups, etc)
      - `domain`: setup for DDD, mediatr, domain pipeline behaviour
      - `infrastructure`: setup for common cross-cutting concerns (auth, versioning, data access, etc)
    - `src`: contains mostly business logic(.NET), use setup code from core
      - `contracts`: common contracts between services
      - `location`: location microservice
      - `profile`: user profile microservice
      - `IdentityProvider` project: not yet created
      - `ApplicationGateway` project: not yet created