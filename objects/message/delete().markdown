```ts
commands.raw('say', async function (message) {
  await message.delete();
  // deleted the original message
  
  await message.reply(message.content.replace('!say', ''));
  // Sends the content you defined
  // we remove the !say because else everything you say with this command would have 
  // a !say at the beginning
});
```
