```ts
commands.raw('locale', async function (message) {
  const guild = await discord.getGuild();

  await message.reply(guild.preferredLocale ?? 'No preffered Locale');
});
```
