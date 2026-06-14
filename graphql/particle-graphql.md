# Particle IoT GraphQL Schema

## Overview

This document describes a conceptual GraphQL schema for the Particle IoT platform. Particle exposes its Device Cloud capabilities primarily through a REST API at `https://api.particle.io`. This GraphQL schema represents the same domain — devices, fleets, events, firmware, SIM cards, integrations, and access control — modeled as a typed graph that enables clients to fetch exactly the fields they need in a single request.

Particle does not currently publish an official GraphQL endpoint. This schema is a conceptual representation derived from the official REST API reference at https://docs.particle.io/reference/cloud-apis/api/ and the GitHub organization at https://github.com/particle-iot. It is intended as a design artifact and developer reference.

## Schema Source

- REST API reference: https://docs.particle.io/reference/cloud-apis/api/
- GitHub organization: https://github.com/particle-iot
- Developer portal: https://www.particle.io/developer-tools/

## Authentication

Particle uses OAuth 2.0 bearer tokens. All GraphQL operations would require an `Authorization: Bearer <token>` header. Tokens are scoped and may be restricted to specific devices, products, or operations.

## Core Domain Areas

### Devices and Fleets

The central resource in Particle is the `Device`. Devices belong to `Product` fleets and may be organized into `DeviceGroup` segments. Fleet-level operations (firmware targeting, configuration, event routing) are modeled through `Fleet` and `FleetOwnership`.

### Events

Particle's publish/subscribe system is modeled through `Event`, `EventStream`, and `EventSubscription`. Devices publish named events with optional payloads; subscribers (webhooks or server-sent event streams) receive them.

### Firmware

Over-the-air (OTA) firmware management is modeled through `FirmwareVersion`, `ProductFirmware`, `FirmwareOTAJob`, and `OTAResult`. Jobs target individual devices or device groups.

### Variables and Functions

Device-exposed state and remote procedure calls are modeled as `Variable`, `VariableRequest`, `Function`, and `FunctionCall`.

### Cloud Code

Particle's serverless compute layer is represented by `CloudCode` and `CloudCodeFunction`.

### SIM Cards

Cellular connectivity management is modeled through `SIM`, `SIMActivation`, and `SimDataUsage`.

### Networks

Private device networks (mesh, VLAN, or cellular private APN) are represented by `Network`, `NetworkDevice`, and `NetworkConfiguration`.

### Integrations and Webhooks

Outbound data routing to third-party services is modeled through `Integration`, `Webhook`, and `WebhookLog`.

### Access Control

OAuth clients, tokens, customers, teams, and organizations form the access-control layer: `OAuth2Client`, `OAuth2Token`, `Customer`, `CustomerDeviceMapping`, `User`, `Team`, `TeamMember`, `Organization`, and `APIToken`.

### Ledger

Particle Ledger is a key-value store that allows cloud-to-device and device-to-cloud data sync. It is modeled through `Ledger` and `LedgerInstance`.

### Diagnostics and Observability

Device telemetry, logs, reconnection events, and usage records are modeled through `DeviceLog`, `UsageRecord`, `DiagnosticEvent`, `PinholeEvent`, `ReconnectionEvent`, and `BackfillEvent`.

### Subscriptions

Account-level billing subscriptions are modeled through `Subscription`.

## Types Summary

| Type | Description |
|------|-------------|
| `Device` | A Particle hardware module connected to the Device Cloud |
| `DeviceGroup` | A named segment of devices within a product fleet |
| `DeviceInfo` | Extended diagnostic and metadata for a device |
| `FirmwareVersion` | A specific firmware binary with version metadata |
| `Fleet` | A logical grouping of products under a single management context |
| `FleetOwnership` | Ownership and access record linking a fleet to an org or user |
| `Product` | A Particle product (fleet of devices sharing firmware and config) |
| `ProductFirmware` | A firmware binary uploaded to a product |
| `ProductDevice` | The representation of a device within a specific product context |
| `ProductGroup` | A device group scoped to a product |
| `Event` | A publish/subscribe event emitted by a device or the cloud |
| `EventStream` | A server-sent event stream subscription handle |
| `EventSubscription` | A persistent subscription configuration for events |
| `Function` | A function exposed by a device for remote invocation |
| `Variable` | A variable exposed by a device for remote reading |
| `FunctionCall` | The result of calling a remote device function |
| `VariableRequest` | The result of reading a remote device variable |
| `CloudCode` | A serverless function deployed to the Particle cloud |
| `CloudCodeFunction` | An individual function within a cloud code deployment |
| `DeviceLog` | A log entry emitted by a device |
| `UsageRecord` | A data operations usage record for billing |
| `Webhook` | An outbound HTTP integration triggered by events |
| `WebhookLog` | A log entry for a webhook delivery attempt |
| `Integration` | A third-party integration (Webhook, Azure, Google Cloud, etc.) |
| `OAuth2Client` | An OAuth 2.0 client application credential |
| `OAuth2Token` | An OAuth 2.0 access or refresh token |
| `Customer` | An end-user customer of a product (for product-mode auth) |
| `CustomerDeviceMapping` | Association between a customer and a claimed device |
| `SIM` | A SIM card associated with a cellular Particle device |
| `SIMActivation` | An activation record for a SIM card |
| `SimDataUsage` | Data usage statistics for a SIM card |
| `Network` | A private device network |
| `NetworkDevice` | A device member of a private network |
| `NetworkConfiguration` | Configuration settings for a private network |
| `User` | A Particle platform user account |
| `Team` | A team within an organization |
| `TeamMember` | A user's membership in a team |
| `Organization` | A Particle organization grouping multiple products and users |
| `Subscription` | A billing subscription plan |
| `APIToken` | A programmatic API access token |
| `Ledger` | A named cloud-side key-value store for device sync |
| `LedgerInstance` | A device-scoped instance of a ledger with its current values |
| `BackfillEvent` | A historical event replayed during a backfill operation |
| `DiagnosticEvent` | A platform-emitted diagnostic event for a device |
| `PinholeEvent` | A connectivity probe event used for latency and reachability |
| `ReconnectionEvent` | An event recording a device reconnection to the cloud |
| `FirmwareOTAJob` | An over-the-air firmware update job targeting devices or groups |
| `OTAResult` | The outcome of an OTA firmware update attempt on a single device |

## Query Examples

```graphql
# Fetch a device and its current variables
query GetDevice($deviceId: ID!) {
  device(id: $deviceId) {
    id
    name
    online
    lastHeard
    firmwareVersion {
      version
      title
    }
    variables {
      name
      type
    }
    functions {
      name
    }
  }
}

# List all devices in a product
query ListProductDevices($productId: ID!, $page: Int, $perPage: Int) {
  product(id: $productId) {
    id
    name
    devices(page: $page, perPage: $perPage) {
      id
      name
      online
      lastIp
      deviceGroup {
        name
      }
    }
  }
}

# Call a device function
mutation CallFunction($deviceId: ID!, $functionName: String!, $argument: String) {
  callFunction(deviceId: $deviceId, name: $functionName, argument: $argument) {
    returnValue
    connected
    calledAt
  }
}

# Read a device variable
query ReadVariable($deviceId: ID!, $variableName: String!) {
  variable(deviceId: $deviceId, name: $variableName) {
    name
    result
    coreInfo {
      lastHeard
      connected
    }
  }
}

# List active OTA jobs for a product
query ListOTAJobs($productId: ID!) {
  product(id: $productId) {
    firmwareOTAJobs {
      id
      targetVersion
      status
      startedAt
      results {
        deviceId
        success
        updatedAt
      }
    }
  }
}
```
