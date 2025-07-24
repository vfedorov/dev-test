# SSE Feature

Server-Sent Events implementation which includes both client-side and server-side utilities to establish SSE connections and manage real-time communication.

## API Reference for backend integration

### Send to all

#### `sendToAllMessage(event, data, exclude?)`

Send a message to all active clients with a possibility to exclude some of them (optional):

```typescript
await sendToAllMessage(
  "messsage",
  {
    message: "Sample message for all active connections",
    type: "warning",
  },
  ["client:id-2", "client:id-3"],
); 
```

### Send to a specific user

#### `sendUserMessage(userId, event, data)`

Send a message to a specific user.

```typescript
await sendUserMessage("user:id-1", "message", {
  title: "Sample message title",
  message: "Sample message text",
  type: "info",
});
```

### Send a message to a group of users

#### `sendToClients(clientIds, event, data)`

Send a message to specific clients by their IDs.

```typescript
await sendToClients(["client:id-5", "cliend:id-6"], "message", {
  message: "Session expired, please login again.",
  type: "warning",
});
```

### Get a number of active users

#### `getClientCount()`

Get a current number of connected clients.

```typescript
const count = getClientCount();
console.log(`${count} active connections`);
```
