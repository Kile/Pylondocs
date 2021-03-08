```ts
commands.raw('pin', async function (message) {
  await message.setPinned(true);
  
  // Pins the message to the channel
  // Change true to false to unpin a message
  // Careful! You should restrict this command
});
```
