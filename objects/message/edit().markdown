```ts
commands.raw('timer', async function (message) {
  const msg = await message.reply('Timer started: 10 seconds');
  
  await sleep(10000);
  // Pylon waits for 10 seconds
  // Note: Pylon can't sleep more than 20 seconds and I wouldn't recommend
  // 20 seconds since if you do something after that it will probably hit
  // the limit and that will result in an error
  
  await msg.edit('Time is up!');
  // Edit the message Pylon send 10 seconds ago
  // Remember: Pylon can only edit it's own messages
});
```
