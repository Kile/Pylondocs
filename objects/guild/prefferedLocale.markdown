```ts
commands.raw('locale', async (message) => {
  let guild = await discord.getGuild();

  await message.reply(guild.preferredLocale ?? 'No preffered Locale');
});
