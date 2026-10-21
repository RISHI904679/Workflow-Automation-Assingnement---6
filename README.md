# Camunda 8 Leave Request — API Practice

Process ID: `leave-request`

Flow: Start Event → User Task `Approve Leave` → End Event

## Deploy
Import `bpmn/leave-request.bpmn` into Camunda Modeler and deploy it to the Camunda 8 cluster / C8 Run.

## Postman
POST `http://localhost:8080/v2/process-instances`

Header: `Content-Type: application/json`

```json
{
  "processDefinitionId": "leave-request",
  "variables": {
    "employeeName": "Ravi",
    "days": 3
  }
}
```

The response should contain a `processInstanceKey`.

## Verify
Open Operate and confirm the instance is running and waiting at `Approve Leave`, with `employeeName` and `days` visible.

## Viva
1. `processDefinitionId` identifies the deployed process definition; `processInstanceKey` identifies one process instance.
2. A wrong process ID causes the API request to fail because the process definition cannot be found.
3. Starting the process 3 times creates 3 separate instances.

## Submission screenshots
- BPMN diagram.
- Postman request + response showing `processInstanceKey`.
- Operate showing the running instance waiting at `Approve Leave`.
