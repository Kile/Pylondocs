commands.raw('botid', async (message) => {
  let id = await discord.getBotId();

  await message.reply(`ID of <@${id}>: ${id}`);
  //Currently this ID is the same everytime, once you can make your own bot
  //with Pylon though, this will be useful. It also means you can tranfer
  //code you wrote on original Pylon with the bot ID to your own bot
  //without having to change anything => Good code
});
