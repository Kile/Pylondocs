```ts
commands.raw('emojis', async (message) => {
//CAREFUL!! With many emojis this is a giant message that spams the chat. Make sure you restrict it
  let emojilist: Array<string> = []; 

  let guild = await discord.getGuild();

  let emojis = await guild.getEmojis();

  for await (let emoji of emojis) {
    emojilist.push(
      `${emoji.name}: ${emoji.animated ? 'animated' : 'not animated'}`
      //Creates a loop where it adds every emoji that exists to a list with the info if it is
      //animated or not
    );
  }
  await message.reply(
    '**Guild emojis**:\n' +
      emojilist
        .toString()
        .replace(/,/g, '\n')
        .replace(/_/g, '_') ?? 'No emojis'
  );
  //Replies the list
  //I use replace for 1) aestetics 2) some emojis have _ in their name
  //and if discord sees two _s it will make them invisible and alter the text
  //If you however use \ before it, you tell discord to ignore that. This is a useful
  //fact for many other things where this happens :3
});
