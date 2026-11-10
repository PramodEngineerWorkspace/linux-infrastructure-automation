Project: WCP Execution API

Build an enterprise-grade Java Spring Boot application for the Workflow Control Platform.

IMPORTANT BUSINESS RULE:

Juniper is the ONLY authorized mechanism for transferring CSV files into the designated Google Cloud Storage bucket.

The WCP platform must NOT provide:

- CSV upload functionality.
- File upload REST endpoints.
- Manual file submission through React UI.
- Any alternative mechanism for adding incoming CSV files.

Workflow:

1. Juniper transfers CSV files into GCS.
2. Eventarc detects newly created GCS objects.
3. Cloud Run Jobs trigger the Java SQL execution engine.
4. SQL commands execute against Cloud SQL PostgreSQL.
5. Execution metadata, command statuses and logs are persisted.
6. WCP Execution API exposes this information to React UI.

Java Spring Boot API responsibilities:

- Display files received from Juniper.
- Display file processing status.
- Display SQL execution details.
- Display command-level success and failure.
- Display execution history and logs.
- Provide authorized retry functionality for eligible failed commands.
- Provide dashboard metrics.

React UI is strictly a monitoring and execution-management interface. It must not upload or create incoming CSV files.

Use one Java Spring Boot application named wcp-execution-api.

Keep GCS ingestion, Eventarc processing, SQL execution and UI-facing API responsibilities clearly separated.
