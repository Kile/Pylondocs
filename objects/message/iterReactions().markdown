```ts
commands.raw('giveaway', async (message) => {
  const msg = await message.reply(
    'React to this message with ' +
      discord.decor.Emojis.WHITE_CHECK_MARK +
      '! You have 10 seconds'
  );

  await sleep(10000);
  let reactants = await msg.iterReactions(
    discord.decor.Emojis.WHITE_CHECK_MARK
  );
  //This returns a list of the users who reacted with the emoji white check mark

  for await (let user of reactants) {
    userlist.push(user.username);
  }
  //With this loop we make the data usable

  var winner = userlist[Math.floor(Math.random() * userlist.length)];
  if (winner === undefined) {
    winner = 'No winner';
  }

  await message.reply(
    'Total reactions: ' + userlist.length + '\nWinner: ' + winner
  );
});
