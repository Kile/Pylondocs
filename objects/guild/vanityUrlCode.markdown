```ts
commands.raw('vanity', async function (message) {
  const guild = await discord.getGuild();

  await message.reply(
    guild.vanityUrlCode ??
      "This server doesn't have a vanity URL yet (BOOST!!!)"
  );
  // The ?? lets Pylon reply an other thing, in this case, guild.vanityUrlCode doesn't exist (that it is null)
});
```
