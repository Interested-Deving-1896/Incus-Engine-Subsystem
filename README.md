# Incus Engine Subsystem

A Linux, Android, macOS, and Windows Incus-based guest operating-system framework.

This repository is the integration and architecture entry point for the Incus platform components. Component implementations remain in their own repositories; this subsystem records their relationship and provides a stable place for cross-component architecture, integration contracts, and end-to-end validation.

## Component registry

| Component | Platform / scope | Responsibility | Repository |
|---|---|---|---|
| Linux toolkit | Linux | Linux guest and host-side Incus tooling | [incus-linux-toolkit](https://github.com/Interested-Deving-1896/incus-linux-toolkit) |
| Waydroid toolkit | Android / Waydroid | Android guest integration and Waydroid tooling | [incus-waydroid-toolkit](https://github.com/Interested-Deving-1896/incus-waydroid-toolkit) |
| macOS toolkit | macOS | macOS-specific Incus tooling and integration | [Incus-MacOS-Toolkit](https://github.com/Interested-Deving-1896/Incus-MacOS-Toolkit) |
| Windows toolkit | Windows | Windows-specific Incus tooling and integration | [incus-windows-toolkit](https://github.com/Interested-Deving-1896/incus-windows-toolkit) |
| Image server | Cross-platform image infrastructure | Incus image publication and serving | [incus-image-server](https://github.com/Interested-Deving-1896/incus-image-server) |

The machine-readable registry is maintained in [components.yml](components.yml).

## Integration principles

- **Repository ownership stays explicit.** Each component repository remains independently versioned and is the source of truth for its implementation.
- **Cross-platform contracts belong here.** Shared interfaces, compatibility matrices, integration tests, and subsystem-level documentation should be coordinated from this repository.
- **No implicit code vendoring.** Registering a component does not copy, rewrite, or merge its source tree into this repository.
- **Incus remains the common engine.** Platform toolkits integrate with the Incus engine while preserving platform-specific packaging and lifecycle behavior.
- **Image infrastructure is a first-class component.** The image server is part of the subsystem architecture, not an unrelated utility.

## Planned integration work

1. Define versioned interfaces between the platform toolkits and image infrastructure.
2. Add a compatibility matrix covering Incus versions, host platforms, guest targets, and image formats.
3. Add cross-repository integration checks and release coordination.
4. Document the build, image publication, provisioning, and guest lifecycle paths end-to-end.

## Ecosystem automation

The subsystem is registered with [Fork-Sync-All](https://github.com/Interested-Deving-1896/fork-sync-all) for the `infra-core` profile. OSP/OOC mirror setup is managed centrally by the Fork-Sync-All mirror workflows; this repository does not independently push to downstream mirrors.
