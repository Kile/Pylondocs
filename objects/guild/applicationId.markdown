```ts
commands.raw('applicationId', async function (message) {
  const guild = await discord.getGuild();

  await message.reply(guild.applicationId ?? 'No application Id');
  // The ?? lets Pylon reply an other thing if, in this case, guild.applicationId doesn't exist
});
```
