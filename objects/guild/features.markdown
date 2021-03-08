```ts
commands.raw('features', async function (message) {
  const guild = await discord.getGuild();

  await message.reply(
    guild.features
      .toString()
      .replace(/,/g, '\n')
      .replace(/_/g, ' ')
  );
  // Giving you a list of what features this servers has enabled, the .replace() stuff to make
  // it prettier, try it out without them to see the difference
});
```
