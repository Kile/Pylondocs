```ts
var userlist = [];
commands.raw('Giveaway', async (message) => {
  const msg = await message.reply(
    'React to this message with ' +
      discord.decor.Emojis.WHITE_CHECK_MARK +
      '! You have 10 seconds'
  );

  await sleep(10000);
  let reactants = await msg.iterReactions(
    discord.decor.Emojis.WHITE_CHECK_MARK
  );

  for await (let user of reactants) {
    userlist.push(user.username);
  }

  await message.reply(
    'Total reactions: ' +
      userlist.length +
      '\nWinner: ' +
      userlist[Math.floor(Math.random() * userlist.length)] ?? 'No winner'
  );
});
