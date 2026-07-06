# harn-microsoft-365-connector

Pure-Harn Microsoft 365 connector for Microsoft Graph Drive and Office artifact
workflows.

The initial surface is deliberately connector-shaped, not document-renderer
shaped:

- Normalize Microsoft Graph change notifications into Harn connector events.
- Poll DriveItem delta from a Harn-managed cursor.
- Dispatch common Microsoft Graph Drive and subscription APIs through an
  allowlisted egress layer.
- Build deterministic request descriptors for Office artifact export/import
  flows.

The document rendering and manifest vocabulary stays in `harn-documents`; this
package owns the external Microsoft 365 boundary.

## Provider

- Provider id: `microsoft_365`
- API host: `graph.microsoft.com`
- Recommended scopes for artifact workflows:
  - `Files.Read`
  - `Files.ReadWrite`
  - `Sites.Read.All`
  - `Sites.ReadWrite.All`

## Useful methods

- `drive.items.get`
- `drive.items.list`
- `drive.items.content`
- `drive.items.export`
- `drive.items.putContent`
- `drive.items.createUploadSession`
- `drive.delta`
- `subscriptions.create`
- `subscriptions.delete`
- `subscriptions.renew`
- `artifact.export_request`
- `artifact.import_request`

## References

- Microsoft Graph DriveItem format conversion:
  <https://learn.microsoft.com/en-us/graph/api/driveitem-get-content-format?view=graph-rest-1.0>
- Microsoft Graph upload small files:
  <https://learn.microsoft.com/en-us/graph/api/driveitem-put-content?view=graph-rest-1.0>
- Microsoft Graph upload sessions:
  <https://learn.microsoft.com/en-us/graph/api/driveitem-createuploadsession?view=graph-rest-1.0>
- Microsoft Graph subscriptions:
  <https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0>
- Microsoft Graph DriveItem delta:
  <https://learn.microsoft.com/en-us/graph/api/driveitem-delta?view=graph-rest-1.0>

## Validation

```sh
harn connector test . --provider microsoft_365
```

The smoke tests use Harn HTTP mocks and do not call Microsoft APIs.
