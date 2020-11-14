```ts
commands.raw('', async (message) => {
  let guild = await discord.getGuild();

  await message.reply(
    'People banned from this guild: ' +
      (await guild.getBans()).length.toString()
  );

  //Checks the length of the array containing the banned people => The number of bans
});
