```ts
commands.raw('joinchannel', async (message) => {
  let guild = await discord.getGuild();
  try {
    var joinchannel = await guild.getChannel(guild.systemChannelId);
    //The joinchannel is where messages are displayed like: -> Kile joined the party
  } catch (e) {
    //In case getChannel throws an error (most likely that there is no channel found)
    //The following will happen
    return message.reply('No system join added');
    //return is here to not continue with the rest of the command
  }
  await message.reply(
    'Join channl name: ' +
      joinchannel?.name +
      '\nJoin channnel Id: ' +
      joinchannel?.id
  );
  //Giving some info about the joinchannel
});
