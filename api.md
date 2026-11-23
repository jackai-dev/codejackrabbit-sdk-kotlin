# CodeJackRabbit Kotlin API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImIwNjc4MWEyNmM0NDY5ZThmMTI4MzBhMDRkNDU1OTU3YmY2MjBkNDJiOWUxZGYxNTVlOTNlZTAwZjI5M2QxYzkiLCJvcGVyYXRpb25fY291bnQiOjI4LCJyZW5kZXJlciI6ImtvdGxpbiIsInZlcnNpb24iOiIxLjUuMCJ9 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `b06781a26c4469e8f12830a04d455957bf620d42b9e1df155e93ee00f293d1c9`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`ClientOptions(hooks = RequestHooks(...))` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every context is an immutable `HookContext`: no hook can change the request.

`ClientOptions(tracer = ...)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `AuditContextRequest`
- `AuditSnapshotsRequest`
- `ComplianceGateRequest`
- `DeveloperAuditRequest`
- `DeveloperEvidenceRequest`
- `FileChange`
- `FinOpsRequest`
- `ManagedDeveloperIdentity`
- `ManagedDeveloperIdentityRequest`
- `ReviewRequest`
- `WaitlistRequest`

## Resource `analysis`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplQ29udHJhY3REcmlmdCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCIsInBhdGgiOiIvdjEvYW5hbHlzaXMvY29udHJhY3QtZHJpZnQiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiI0NTg5ZGYwYTJiNGU4Zjk0ZjIwMmQ3ODQ0ODk4YTFhM2Y0NzBhMWUyNzgwMDA5ZThlMjAxZmUxY2E5NmU3MDkwIiwic2lnbmF0dXJlX3NoYTI1NiI6ImZiM2E3YzFjMmM0MjVkNjVjODA0NjNkYjkxMTk3M2FiMmIwN2M1ZTc0N2I2MzEwMjc3NGI3OTU5N2I4MDI0NGEifQ -->
### `client.analysis.analyzeContractDrift`

Operation ID: `analyzeContractDrift`  
Route: `POST` `/v1/analysis/contract-drift`  
Equivalent member: `client.analyzeContractDrift`  

#### Signature

```kotlin
suspend fun analyzeContractDrift(params: AnalyzeContractDriftParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Contract drift report and SemVer recommendation | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.analysis.analyzeContractDrift(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplQ29udHJhY3REcmlmdCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5hbmFseXplUGVyZkZpbk9wcyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyIsInBhdGgiOiIvdjEvYW5hbHlzaXMvcGVyZi1maW5vcHMiLCJyZXNvdXJjZSI6ImFuYWx5c2lzIiwic2VjdGlvbl9zaGEyNTYiOiIzMDY2MTNhYzlmYTExN2VhMDRiZjAzYTczMzhkY2UyZDYwOWI1ZGZhMTBmMTIxNWExZmFlNDRiODMwMzRiMWYxIiwic2lnbmF0dXJlX3NoYTI1NiI6ImQ5NTBmZmUyOGVjMTUyNThmZjU0Y2ZmODA5NDQzMTYxMzAxZGQyM2QxNjNlYjczYjJiOGIxNmI2MjkwYzQxZjUifQ -->
### `client.analysis.analyzePerfFinOps`

Operation ID: `analyzePerfFinOps`  
Route: `POST` `/v1/analysis/perf-finops`  
Equivalent member: `client.analyzePerfFinOps`  

#### Signature

```kotlin
suspend fun analyzePerfFinOps(params: AnalyzePerfFinOpsParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Performance and FinOps audit report | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.analysis.analyzePerfFinOps(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplUGVyZkZpbk9wcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXNpcy5wbGFuU3RhY2tlZFByU3BsaXQiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicGxhblN0YWNrZWRQclNwbGl0IiwicGF0aCI6Ii92MS9hbmFseXNpcy9zcGxpdC1wciIsInJlc291cmNlIjoiYW5hbHlzaXMiLCJzZWN0aW9uX3NoYTI1NiI6ImI1YTNmZjgzOTg0NzkxNzFhMDhmMmZlNmJmODBhYzA3MWVjNjZiMDU4MzYzOTY2ZmYyNGFkOTQ0MzU2MzU1MWUiLCJzaWduYXR1cmVfc2hhMjU2IjoiYjQyNWNlNzExYzg2ZDU5NmVlM2ViNTY0YTcwMmQ1MzI3NDFjNGRmMTlhYTAyZTIxZTU0MzA0ZjgxMTRmMTYzYSJ9 -->
### `client.analysis.planStackedPrSplit`

Operation ID: `planStackedPrSplit`  
Route: `POST` `/v1/analysis/split-pr`  
Equivalent member: `client.planStackedPrSplit`  

#### Signature

```kotlin
suspend fun planStackedPrSplit(params: PlanStackedPrSplitParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Ordered stacked PR plan and git commands | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.analysis.planStackedPrSplit(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwbGFuU3RhY2tlZFByU3BsaXQifQ -->

## Resource `analytics`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhbmFseXRpY3MuZ2V0QW5hbHl0aWNzUm9pIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QW5hbHl0aWNzUm9pIiwicGF0aCI6Ii92MS9hbmFseXRpY3Mvcm9pIiwicmVzb3VyY2UiOiJhbmFseXRpY3MiLCJzZWN0aW9uX3NoYTI1NiI6ImE5OWQyMmQxMjYxMzE2MmEzOWFiNzViZmUxNmYyYjgwNTQ1ZTQwMzAxODcwMWQ4NzcxODc5MWFkNjUzY2Q2YTEiLCJzaWduYXR1cmVfc2hhMjU2IjoiMjEzNTQ4M2UxYmUzYzE0NjQ2N2E0YjQ5OGJhM2NmMzIyNGE2OTVjNDVjZjk2MDdiMGExYzU0ZjkwNmRkZWZkNiJ9 -->
### `client.analytics.getAnalyticsRoi`

Operation ID: `getAnalyticsRoi`  
Route: `GET` `/v1/analytics/roi`  
Equivalent member: `client.getAnalyticsRoi`  

#### Signature

```kotlin
suspend fun getAnalyticsRoi(params: GetAnalyticsRoiParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | ROI telemetry summary | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.analytics.getAnalyticsRoi()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBbmFseXRpY3NSb2kifQ -->

## Resource `capabilities`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjYXBhYmlsaXRpZXMuZ2V0Q2FwYWJpbGl0aWVzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0Q2FwYWJpbGl0aWVzIiwicGF0aCI6Ii92MS9jYXBhYmlsaXRpZXMiLCJyZXNvdXJjZSI6ImNhcGFiaWxpdGllcyIsInNlY3Rpb25fc2hhMjU2IjoiOTBiYWY5ZTBiYTY4YTJmMzhiMTI3N2M4NDAwMTE3YTU4ODU3ZDIzYThiYTYyNGRiZTM2NDMyOWExMWUyNzk4ZCIsInNpZ25hdHVyZV9zaGEyNTYiOiJhNDU1YjhjZmViYzRiZDc0MWUxOTZmZGE4M2RiNmJkNGQ4NGViMWQyYWRjNGM2M2RhYzEwMzQ1ODkwMzNkZDFjIn0 -->
### `client.capabilities.getCapabilities`

Operation ID: `getCapabilities`  
Route: `GET` `/v1/capabilities`  
Equivalent member: `client.getCapabilities`  

#### Signature

```kotlin
suspend fun getCapabilities(params: GetCapabilitiesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Capabilities catalog | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.capabilities.getCapabilities()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRDYXBhYmlsaXRpZXMifQ -->

## Resource `compliance`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV2YWx1YXRlQ29tcGxpYW5jZUdhdGUiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiZXZhbHVhdGVDb21wbGlhbmNlR2F0ZSIsInBhdGgiOiIvdjEvY29tcGxpYW5jZS9nYXRlIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJmNmNlMTcyM2E1MjUzYmE1YzI2N2QyZjVmZDc4MjdhOTU2NzcwY2Q2MTE4OWRkYTZmZGZiNGVjODA1ZDE2OWYyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjdjNDY2ODkzYmI0MDc3NmI1YWIxMDdhOTdmMmExMzhkOGU1YjJhYWQ1MDFlN2ZlYWFjZmE2MmFhZjFiY2Q3NWMifQ -->
### `client.compliance.evaluateComplianceGate`

Operation ID: `evaluateComplianceGate`  
Route: `POST` `/v1/compliance/gate`  
Equivalent member: `client.evaluateComplianceGate`  

#### Signature

```kotlin
suspend fun evaluateComplianceGate(params: EvaluateComplianceGateParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ComplianceGateRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Compliance gate verdict and SHA-256 attestation | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.compliance.evaluateComplianceGate(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJldmFsdWF0ZUNvbXBsaWFuY2VHYXRlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJjb21wbGlhbmNlLmV4cG9ydFNhcmlmIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImV4cG9ydFNhcmlmIiwicGF0aCI6Ii92MS9jb21wbGlhbmNlL3NhcmlmIiwicmVzb3VyY2UiOiJjb21wbGlhbmNlIiwic2VjdGlvbl9zaGEyNTYiOiIyY2ZmNDcyNDJjNWRjNjM3MDIwZDgzNDViNWVjMmUxN2Q5YTgzNGYxOTllOGFlNzM3MGM3YzRjYTg3Y2EzOGUxIiwic2lnbmF0dXJlX3NoYTI1NiI6ImU4NDFiNjRmN2EzMGY5YTEwNjAyZTM4NmI2ZTQ5ZTg0YzhmZjJlYjEwZjQ1MGI1NWJiYmQxZDNhZGYwZDljYzEifQ -->
### `client.compliance.exportSarif`

Operation ID: `exportSarif`  
Route: `POST` `/v1/compliance/sarif`  
Equivalent member: `client.exportSarif`  

#### Signature

```kotlin
suspend fun exportSarif(params: ExportSarifParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | SARIF 2.1.0 JSON document | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.compliance.exportSarif(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJleHBvcnRTYXJpZiJ9 -->

## Resource `developerIntelligence`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UuY29sbGVjdERldmVsb3BlckF1ZGl0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNvbGxlY3REZXZlbG9wZXJBdWRpdCIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWF1ZGl0IiwicmVzb3VyY2UiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjVmNzk0YTdlYWQ4ZTY3YjFjZDM3ODQxNGNkNDQwYzhlZDBiYzZmZmY1MTYwZDhmZjk2MTAzM2I0YzcyNGY5YTMiLCJzaWduYXR1cmVfc2hhMjU2IjoiY2JjN2I3ZWM0OTI2ZGRhZWM5OTVmYWYxMDE0ZjdkM2YzZjQ4Njc4NGFlNWQ1Nzg5M2U2MDgyYzdlMTc1NWYxMyJ9 -->
### `client.developerIntelligence.collectDeveloperAudit`

Operation ID: `collectDeveloperAudit`  
Route: `POST` `/cli/managed/developer-audit`  
Equivalent member: `client.collectDeveloperAudit`  

#### Signature

```kotlin
suspend fun collectDeveloperAudit(params: CollectDeveloperAuditParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperAuditRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Versioned report with source coverage, missing evidence and immutable snapshot reference. | application/json (object) |
| `default` | Explicit authentication, paid access, source authorization, capacity or collection blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "from": "2026-01-09",
    "repositoryId": "1",
    "to": "2026-01-18"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.developerIntelligence.collectDeveloperAudit(body = {"from": "2026-01-09", "repositoryId": "1", "to": "2026-01-18"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb2xsZWN0RGV2ZWxvcGVyQXVkaXQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UuY3VycmVudERldmVsb3BlcklkZW50aXR5IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImN1cnJlbnREZXZlbG9wZXJJZGVudGl0eSIsInBhdGgiOiIvY2xpL21hbmFnZWQvZGV2ZWxvcGVyLWlkZW50aXR5IiwicmVzb3VyY2UiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6Ijg3NDhlN2IxMzlmYmY0ZjkyYWZmZDY2ZDY0YjQzY2FkZTgyNjY4OWIwOTBhZDhkYjUwNWY3MDZiYjBiNTY4MDIiLCJzaWduYXR1cmVfc2hhMjU2IjoiNDQ0ZmNmYTcwNzc1NGE5ZmFjYzZmY2QyZDY3YzFkNjY5OGE4YjhmY2Y1YzAxOTdlNzVjMjMzMjY1YTgyYzNhMiJ9 -->
### `client.developerIntelligence.currentDeveloperIdentity`

Operation ID: `currentDeveloperIdentity`  
Route: `POST` `/cli/managed/developer-identity`  
Equivalent member: `client.currentDeveloperIdentity`  

#### Signature

```kotlin
suspend fun currentDeveloperIdentity(params: CurrentDeveloperIdentityParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<ManagedDeveloperIdentity>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ManagedDeveloperIdentityRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Current verified identity and authorized repositories. | application/json (ManagedDeveloperIdentity) |
| `default` | Explicit account, GitHub identity or source authorization blocker. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.developerIntelligence.currentDeveloperIdentity(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjdXJyZW50RGV2ZWxvcGVySWRlbnRpdHkifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UuZGVjbGFyZURldmVsb3BlclByb2plY3RDb250ZXh0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImRlY2xhcmVEZXZlbG9wZXJQcm9qZWN0Q29udGV4dCIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtY29udGV4dCIsInJlc291cmNlIjoiZGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiJhZmE3M2FmZDQxOGU3ZGMwZWYxMTFkM2RkNzBhYzUxNjQ0ZGNiMmQyNjZiYjVlNzE3MTU5NTllODFjNzM0ZGI3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjUxMjY2MTU0ZjUwZDg2MDczMWNmMzNkOTM5MGNlNzdkNWRkM2NhMTFlNzgwMjcwN2M2YTNjZTc2ZmNiMGQ0MmMifQ -->
### `client.developerIntelligence.declareDeveloperProjectContext`

Operation ID: `declareDeveloperProjectContext`  
Route: `POST` `/cli/managed/audit-context`  
Equivalent member: `client.declareDeveloperProjectContext`  

#### Signature

```kotlin
suspend fun declareDeveloperProjectContext(params: DeclareDeveloperProjectContextParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditContextRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Immutable declaration or correction receipt. | application/json (object) |
| `default` | Explicit authorization, contributor identity, correction or storage capacity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "declaration": {
      "contributorId": "1",
      "effectiveFrom": "2026-01-02",
      "effectiveTo": "2026-01-11",
      "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa",
      "source": "example",
      "supersedes": "example",
      "type": "project_join",
      "value": "example"
    },
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.developerIntelligence.declareDeveloperProjectContext(body = {"declaration": {"contributorId": "1", "effectiveFrom": "2026-01-02", "effectiveTo": "2026-01-11", "snapshotId": "aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa", "source": "example", "supersedes": "example", "type": "project_join", "value": "example"}, "repositoryId": "1"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJkZWNsYXJlRGV2ZWxvcGVyUHJvamVjdENvbnRleHQifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UubWFuYWdlZEF1ZGl0U25hcHNob3RzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Im1hbmFnZWRBdWRpdFNuYXBzaG90cyIsInBhdGgiOiIvY2xpL21hbmFnZWQvYXVkaXQtc25hcHNob3RzIiwicmVzb3VyY2UiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UiLCJzZWN0aW9uX3NoYTI1NiI6IjY4NTk5MDU3Y2EwYjUyNjNiMGQ0YWRmY2RmYTJhNjk1MDZhN2NiZmMyMGMwYzhiMWI1ZmYxNmI1NmVmNTI5NGMiLCJzaWduYXR1cmVfc2hhMjU2IjoiNzBkOThjYjJlM2RmNjhjMGM4ZWZkYWEzN2I0M2MzNWNkOGU5ZjBkY2JhZTBkYjU2MWQ3YmQ4ZjQyY2I1YzM3ZSJ9 -->
### `client.developerIntelligence.managedAuditSnapshots`

Operation ID: `managedAuditSnapshots`  
Route: `POST` `/cli/managed/audit-snapshots`  
Equivalent member: `client.managedAuditSnapshots`  

#### Signature

```kotlin
suspend fun managedAuditSnapshots(params: ManagedAuditSnapshotsParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `AuditSnapshotsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot list or digest-verified immutable envelope. | application/json (object) |
| `default` | Explicit authorization, expiry, missing snapshot or integrity blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "list",
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.developerIntelligence.managedAuditSnapshots(body = {"action": "list", "repositoryId": "1"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJtYW5hZ2VkQXVkaXRTbmFwc2hvdHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2UucHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicHJvdmlkZXJDb3N0RXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2Zpbm9wcyIsInJlc291cmNlIjoiZGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI5MDJlZmMyYWUyN2FlZjgyMjQxNDY4ZmQzYjc1OTk5OTQ4NjQ4NGI4YmM3MTYyNWE5MjZkZWIwMDdiMGFhNWQ2Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImUzYmI0YjRkNjBjYTJlNDNlZTRlOTM5ZWMzYjkwYzVkYmQxMTY3NzU3NWNiNTBlZGJiOWE1MTNkYmU5ZWQ2MjkifQ -->
### `client.developerIntelligence.providerCostEvidence`

Operation ID: `providerCostEvidence`  
Route: `POST` `/cli/managed/finops`  
Equivalent member: `client.providerCostEvidence`  

#### Signature

```kotlin
suspend fun providerCostEvidence(params: ProviderCostEvidenceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `FinOpsRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server report or declaration receipt. Unknown costs remain null. | application/json (object) |
| `default` | Explicit permission, paid access, source or declaration validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "action": "report"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.developerIntelligence.providerCostEvidence(body = {"action": "report"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aWRlckNvc3RFdmlkZW5jZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJkZXZlbG9wZXJJbnRlbGxpZ2VuY2Uuc3VibWl0RGV2ZWxvcGVyRXZpZGVuY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3VibWl0RGV2ZWxvcGVyRXZpZGVuY2UiLCJwYXRoIjoiL2NsaS9tYW5hZ2VkL2RldmVsb3Blci1ldmlkZW5jZSIsInJlc291cmNlIjoiZGV2ZWxvcGVySW50ZWxsaWdlbmNlIiwic2VjdGlvbl9zaGEyNTYiOiI0ZjFiYzBiZDQwYTA1NjJhZTRiZjc2ZjE5ODM4ODRkM2ZhMzBkY2FjYjgxM2MyNzc3OTk2NGUxYjA3NjI3YzVhIiwic2lnbmF0dXJlX3NoYTI1NiI6ImZlZDRhNDUxNjUzN2QzZmVhYjdjZTdkNzI3MjQ3MzIxNTkxZjRhMjJhMTY5YWFkZDQ3NzA0OWNlNjkyMjJlMzEifQ -->
### `client.developerIntelligence.submitDeveloperEvidence`

Operation ID: `submitDeveloperEvidence`  
Route: `POST` `/cli/managed/developer-evidence`  
Equivalent member: `client.submitDeveloperEvidence`  

#### Signature

```kotlin
suspend fun submitDeveloperEvidence(params: SubmitDeveloperEvidenceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `DeveloperEvidenceRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Accepted and duplicate span counts. | application/json (object) |
| `default` | Explicit identity, repository, paid access or evidence validation blocker. | none |

#### Canonical required-input example

```json
{
  "body": {
    "category": "coding",
    "input": {},
    "repositoryId": "1"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.developerIntelligence.submitDeveloperEvidence(body = {"category": "coding", "input": {}, "repositoryId": "1"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXREZXZlbG9wZXJFdmlkZW5jZSJ9 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0SGVhbHRoIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiNGIyNTYzNWFiOTYyOWJiZDExZDM5OTIwZjA1MGE5ZGY0NzZjNjZiYjkyOWU2NzA1YjRiZWZmNTg4NGU0Njg2OSIsInNpZ25hdHVyZV9zaGEyNTYiOiI2NGNhZmRlNGUzMWFmNWIxMDMxYjZmYjk5ZWFlMWRkMGJmZWJkMzhiMGExYWRjMmIyYzJjY2JhNWU3ZWZiNDcyIn0 -->
### `client.health.getHealth`

Operation ID: `getHealth`  
Route: `GET` `/health`  
Equivalent member: `client.getHealth`  

#### Signature

```kotlin
suspend fun getHealth(params: GetHealthParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Server health status | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.health.getHealth()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `reviews`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmJ1aWxkQXV0b2ZpeEJ1bmRsZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUiLCJwYXRoIjoiL3YxL3Jldmlld3MvYXV0b2ZpeCIsInJlc291cmNlIjoicmV2aWV3cyIsInNlY3Rpb25fc2hhMjU2IjoiY2JiMzVkNDEwOTk2Y2Q2OTdmY2E4MjNiMWY0MjUyOTVhMTJhYzFiY2VkMzZhNjAwOTM2MjczNWQ0ZjdkMjUwYyIsInNpZ25hdHVyZV9zaGEyNTYiOiIyZjI3Nzc4M2IwODg2ZWRmMjExNjEwOTE3OTZmMDRhYzk4NmMyNWMyOWNhZmM3YzAyNTMyODk4MzY4NTYyYWZmIn0 -->
### `client.reviews.buildAutofixBundle`

Operation ID: `buildAutofixBundle`  
Route: `POST` `/v1/reviews/autofix`  
Equivalent member: `client.buildAutofixBundle`  

#### Signature

```kotlin
suspend fun buildAutofixBundle(params: BuildAutofixBundleParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Remediation patch bundle | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.reviews.buildAutofixBundle(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJidWlsZEF1dG9maXhCdW5kbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNvbXB1dGVSaXNrUmFkYXIiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY29tcHV0ZVJpc2tSYWRhciIsInBhdGgiOiIvdjEvcmV2aWV3cy9yaXNrLXJhZGFyIiwicmVzb3VyY2UiOiJyZXZpZXdzIiwic2VjdGlvbl9zaGEyNTYiOiJkNDk2OTlmMjA1YWE2NmZiZjYyZTYyM2QwMTE4YTRkZDk2ZjZjNDZhMzQ3ZDM4ODk3NTk1YjZkMmEyMjE0ZmUxIiwic2lnbmF0dXJlX3NoYTI1NiI6IjIzODhmMmNkZjE2MDU5OWE2OGZjNjA0OWQ4MWQxYTk1ZDdkNTNmMDEwMDkxNzI5NmI0MzQyOWQwYjEzMGMwZWEifQ -->
### `client.reviews.computeRiskRadar`

Operation ID: `computeRiskRadar`  
Route: `POST` `/v1/reviews/risk-radar`  
Equivalent member: `client.computeRiskRadar`  

#### Signature

```kotlin
suspend fun computeRiskRadar(params: ComputeRiskRadarParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | 6-axis Risk Radar telemetry | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.reviews.computeRiskRadar(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb21wdXRlUmlza1JhZGFyIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJyZXZpZXdzLmNyZWF0ZVJldmlldyIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXciLCJwYXRoIjoiL3YxL3Jldmlld3MiLCJyZXNvdXJjZSI6InJldmlld3MiLCJzZWN0aW9uX3NoYTI1NiI6Ijc1ZmI4NDQwMTlhZjQ4MzM4NjRkNGI3OTVlNWVjZTA1YTJlNjNlZjZlZWI0NTI4ZDA5YmY0MWYwOTEzZmI2MGIiLCJzaWduYXR1cmVfc2hhMjU2IjoiN2MyNjc4NDExZDUwMjc0ZGQxZTkzOGEyNmMxZmM3ZmY5NDI4YjBmNDFiNGFmMTBmMTUxMmYwNWNjNDQwODY5ZiJ9 -->
### `client.reviews.createReview`

Operation ID: `createReview`  
Route: `POST` `/v1/reviews`  
Equivalent member: `client.createReview`  

#### Signature

```kotlin
suspend fun createReview(params: CreateReviewParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Completed review result with findings, blast radius, and change stack | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.reviews.createReview(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVSZXZpZXcifQ -->

## Resource `saas`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmZpbmFsaXplTWV0ZXJpbmdRdW90YSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEiLCJwYXRoIjoiL3YxL3NhYXMvbWV0ZXJpbmcvZmluYWxpemUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6IjE3Njk2NjA0MTA3MGNkMGFhOGNlNTljOTI1ZTg0MGNkNGY1Y2EyMzBlZDVkY2E5ZGMwZTI5MzUzMWIyMWM1ZWUiLCJzaWduYXR1cmVfc2hhMjU2IjoiOTc2NWU4MDFkODM5MjAxOTYwZWIzMmIyMDk1OGQyNWQwNTQ3MWE0OTY4ZWExMDkwZGM3ZTk5ZmZhNjM5YzgxMyJ9 -->
### `client.saas.finalizeMeteringQuota`

Operation ID: `finalizeMeteringQuota`  
Route: `POST` `/v1/saas/metering/finalize`  
Equivalent member: `client.finalizeMeteringQuota`  

#### Signature

```kotlin
suspend fun finalizeMeteringQuota(params: FinalizeMeteringQuotaParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Finalized metering settlement | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.saas.finalizeMeteringQuota(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJmaW5hbGl6ZU1ldGVyaW5nUXVvdGEifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmdldFNhYXNCbHVlcHJpbnQiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50IiwicGF0aCI6Ii92MS9zYWFzL2JsdWVwcmludCIsInJlc291cmNlIjoic2FhcyIsInNlY3Rpb25fc2hhMjU2IjoiOGZmZTYyOWI4OWRlOTBmZDc1NThjZGZiMTI1NmRiOWI5MmY1ZDVjOTE5YTNkMGIxZjFkYzc0ODljZjk0MDI4ZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MDM2YjIxZDczZDRlNjk1NDdiZGYzM2M5MDNkZThhZWRhNzYzY2FlOTUwMzVmYTg3NWFhYzUyNTM2ZDNiN2VmIn0 -->
### `client.saas.getSaasBlueprint`

Operation ID: `getSaasBlueprint`  
Route: `GET` `/v1/saas/blueprint`  
Equivalent member: `client.getSaasBlueprint`  

#### Signature

```kotlin
suspend fun getSaasBlueprint(params: GetSaasBlueprintParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Autonomous SaaS blueprint | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.saas.getSaasBlueprint()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRTYWFzQmx1ZXByaW50In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLmlzc3VlU3VyZmFjZUxlYXNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6Imlzc3VlU3VyZmFjZUxlYXNlIiwicGF0aCI6Ii92MS9zYWFzL3N1cmZhY2UtbGVhc2UvaXNzdWUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6ImU2NzFkOTcxODRjYzY5ZDI2ZDc0YjM3YjI4ZWY3OWUxZjUxYzVkODE5Yjc5N2U3NDc3OWZmMDNjMDBlZjU0MmIiLCJzaWduYXR1cmVfc2hhMjU2IjoiNjM3Nzg2MDY3MzAwYjBkMDdmNzMzNTgyNWNjNDM4Yzk4N2VlZGE0OGFlMjc3NWU5NzgwMWVmMTI2MGJlMWEyNyJ9 -->
### `client.saas.issueSurfaceLease`

Operation ID: `issueSurfaceLease`  
Route: `POST` `/v1/saas/surface-lease/issue`  
Equivalent member: `client.issueSurfaceLease`  

#### Signature

```kotlin
suspend fun issueSurfaceLease(params: IssueSurfaceLeaseParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Issued surface lease token | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.saas.issueSurfaceLease(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpc3N1ZVN1cmZhY2VMZWFzZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYWFzLnJlc2VydmVNZXRlcmluZ1F1b3RhIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlc2VydmVNZXRlcmluZ1F1b3RhIiwicGF0aCI6Ii92MS9zYWFzL21ldGVyaW5nL3Jlc2VydmUiLCJyZXNvdXJjZSI6InNhYXMiLCJzZWN0aW9uX3NoYTI1NiI6ImMxYjdmYTFjNTE5NjJjNTAwNTBkMTNkNjgxZjUyNDA3YWZmZTFiZjFjNzExYjM2YjhjZGFjYTUyYWFlY2Q5MmUiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWY5OGU3Y2E0ZTQxNzI5N2MyNWQyZTA2ZTFlMmVlMzljMTk3YzAzMTQwN2RmMDYxMDU3ZjE1NGUyNzQyNzY4OSJ9 -->
### `client.saas.reserveMeteringQuota`

Operation ID: `reserveMeteringQuota`  
Route: `POST` `/v1/saas/metering/reserve`  
Equivalent member: `client.reserveMeteringQuota`  

#### Signature

```kotlin
suspend fun reserveMeteringQuota(params: ReserveMeteringQuotaParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Metering reservation record | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.saas.reserveMeteringQuota(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXNlcnZlTWV0ZXJpbmdRdW90YSJ9 -->

## Resource `sbom`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzYm9tLmdlbmVyYXRlU2JvbSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20iLCJwYXRoIjoiL3YxL3Nib20iLCJyZXNvdXJjZSI6InNib20iLCJzZWN0aW9uX3NoYTI1NiI6IjdmNjZjZTQwY2E3NmQzOWMyMDE4YmM5Y2ZlYTQ4ZTI4ZWY1MWYyZGM0NmE3MThiYjA1MzQ2ZDIzZWIxNjhmYjciLCJzaWduYXR1cmVfc2hhMjU2IjoiNzM4NmYwZjE4YzFkNzQ3NTEzNjA2YWRmYTA3MGRkY2EzZGNkOGU4MTM0MmNkYWZiMjIzNzdlMzNmYzY2NTUzZiJ9 -->
### `client.sbom.generateSbom`

Operation ID: `generateSbom`  
Route: `POST` `/v1/sbom`  
Equivalent member: `client.generateSbom`  

#### Signature

```kotlin
suspend fun generateSbom(params: GenerateSbomParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | CycloneDX 1.5 SBOM JSON | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.sbom.generateSbom(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZW5lcmF0ZVNib20ifQ -->

## Resource `supplyChain`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJzdXBwbHlDaGFpbi5hbmFseXplU3VwcGx5Q2hhaW4iLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiYW5hbHl6ZVN1cHBseUNoYWluIiwicGF0aCI6Ii92MS9zdXBwbHktY2hhaW4vYW5hbHl6ZSIsInJlc291cmNlIjoic3VwcGx5Q2hhaW4iLCJzZWN0aW9uX3NoYTI1NiI6ImM4YjU3ZTVkMGVjYmY3NDUwZWI1MGFjMTc2MjAyMWEzMDg4OGNmZjdlOGQ1NTE4NTFmMjViODEzOWM4NGNmNjQiLCJzaWduYXR1cmVfc2hhMjU2IjoiNmExZWUyZmQyMDY4YzRlYmI4YTViM2FmYjdkY2EwOTAyMjM4YmJhMDc0ZWM5OTdhNmRkOWFjMGVjMzkxZGQ1NyJ9 -->
### `client.supplyChain.analyzeSupplyChain`

Operation ID: `analyzeSupplyChain`  
Route: `POST` `/v1/supply-chain/analyze`  
Equivalent member: `client.analyzeSupplyChain`  

#### Signature

```kotlin
suspend fun analyzeSupplyChain(params: AnalyzeSupplyChainParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `ReviewRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Supply-chain security audit | none |

#### Canonical required-input example

```json
{
  "body": {
    "files": [
      {
        "filename": "example"
      }
    ]
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.supplyChain.analyzeSupplyChain(body = {"files": [{"filename": "example"}]})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJhbmFseXplU3VwcGx5Q2hhaW4ifQ -->

## Resource `tasks`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5jcmVhdGVDb2RpbmdUYXNrIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUNvZGluZ1Rhc2siLCJwYXRoIjoiL3YxL3Rhc2tzIiwicmVzb3VyY2UiOiJ0YXNrcyIsInNlY3Rpb25fc2hhMjU2IjoiOGZjYTM0MGM3NGEyODBiZTUxODFhMmQ4MDZlMjg1MzYyNjEyNmNiOWY2ZWRlOThlYzhiNTVlYjIxZmE4ZmZjNyIsInNpZ25hdHVyZV9zaGEyNTYiOiJlNzM5ZTI1NzYxOTEwMWQ4MzgzZjIxYjg5ZWE3YzFmMThiYjBlZGM1ZGEyNDE1ZmQyNGE4OTNjNzQ1ZDJmYjQzIn0 -->
### `client.tasks.createCodingTask`

Operation ID: `createCodingTask`  
Route: `POST` `/v1/tasks`  
Equivalent member: `client.createCodingTask`  

#### Signature

```kotlin
suspend fun createCodingTask(params: CreateCodingTaskParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Created coding task | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.tasks.createCodingTask(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDb2RpbmdUYXNrIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0YXNrcy5saXN0Q29kaW5nVGFza3MiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MiLCJwYXRoIjoiL3YxL3Rhc2tzIiwicmVzb3VyY2UiOiJ0YXNrcyIsInNlY3Rpb25fc2hhMjU2IjoiMGY0NDhiZGY5MzhlOThhZjU0ZDg3MmNhZDZlNDQwMGU0MjBjOGQ3NzcyMDg1MDY1NDA2N2JiMDYzYzVkOTgyNCIsInNpZ25hdHVyZV9zaGEyNTYiOiI3NzAzM2Q3OWRiNjk2NTQ4ZmNmOWQ1ZDIwNWVjNjFiOTI5NTdlMjM4MTkyMjc0NDZjNjk3NWI2NjM0YWE4ZDM5In0 -->
### `client.tasks.listCodingTasks`

Operation ID: `listCodingTasks`  
Route: `GET` `/v1/tasks`  
Equivalent member: `client.listCodingTasks`  

#### Signature

```kotlin
suspend fun listCodingTasks(params: ListCodingTasksParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Task list | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.tasks.listCodingTasks()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Q29kaW5nVGFza3MifQ -->

## Resource `triage`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0cmlhZ2UuZ2V0VHJpYWdlUXVldWUiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSIsInBhdGgiOiIvdjEvdHJpYWdlIiwicmVzb3VyY2UiOiJ0cmlhZ2UiLCJzZWN0aW9uX3NoYTI1NiI6IjYyYWRhY2ZmNjQ4MmE4N2JkMjY1MzgzZDMxZjAzNjBiMjk4MmRmNTVjNTY3MmE3ZGU0Mjk4ODMyNTA1NjFhMTEiLCJzaWduYXR1cmVfc2hhMjU2IjoiY2Y2MTI3ZTU2YTI2Yzk0ZWEwYjlmZTI3N2M1ZTUxMDk5OGU0NjU2MzJkZjJkNDlkZTNkYTQwZGI2NmJiMTMzNSJ9 -->
### `client.triage.getTriageQueue`

Operation ID: `getTriageQueue`  
Route: `GET` `/v1/triage`  
Equivalent member: `client.getTriageQueue`  

#### Signature

```kotlin
suspend fun getTriageQueue(params: GetTriageQueueParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Triaged PR queue | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.triage.getTriageQueue()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRUcmlhZ2VRdWV1ZSJ9 -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0V2FpdGxpc3QiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QiLCJwYXRoIjoiL3YxL3dhaXRsaXN0IiwicmVzb3VyY2UiOiJ3YWl0bGlzdCIsInNlY3Rpb25fc2hhMjU2IjoiMjQ0NDdlMGRlYjcyNGMwNmU4MTk1YzA5Mzc4MjhkZDUxNDQzZjdiYWZkZjEyNTdmM2ZlNDQ2MmU3ZmU4NjVkYyIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MGRjZTZlMTQ3NzU2ZTIzYTYwYTZlZmVkYzJhYjgyODJjYzQ5YTU1YjBjMGU5ODQyZDkwOThiNDhlOGE3ZDE2In0 -->
### `client.waitlist.listWaitlist`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  
Equivalent member: `client.listWaitlist`  

#### Signature

```kotlin
suspend fun listWaitlist(params: ListWaitlistParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Waitlist entries | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.waitlist.listWaitlist()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZWdpc3RlcldhaXRsaXN0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlZ2lzdGVyV2FpdGxpc3QiLCJwYXRoIjoiL3YxL3dhaXRsaXN0IiwicmVzb3VyY2UiOiJ3YWl0bGlzdCIsInNlY3Rpb25fc2hhMjU2IjoiNWI1YzI0ZDcwMTgyOTYzODRlZjU5NDYzNDBkYTdkNjE0YThjZDc0NTY1ZGFhNmI4MzJhN2JjODQ0MzIxYTFjOSIsInNpZ25hdHVyZV9zaGEyNTYiOiJkZjFlZDQ3ZmMxOTZkNGM3ZDZhMzQyMzc4OTA5ZjY2MGIzM2Y4OTdkMzcwNmU4MmNkZTU2NjNlNjdiOWVhZWE5In0 -->
### `client.waitlist.registerWaitlist`

Operation ID: `registerWaitlist`  
Route: `POST` `/v1/waitlist`  
Equivalent member: `client.registerWaitlist`  

#### Signature

```kotlin
suspend fun registerWaitlist(params: RegisterWaitlistParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `WaitlistRequest` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Waitlist entry created | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-c65f@example.test"
  },
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.waitlist.registerWaitlist(body = {"email": "example-c65f@example.test"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlcldhaXRsaXN0In0 -->

