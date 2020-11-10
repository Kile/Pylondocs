commands.raw('avatar', async (message) => {
  let user = await discord.getUser(message.author.id);
  //You can insert any other ID here, even from people not on the guild
  let avatarurl = await user?.getAvatarUrl();

  await message.reply(
    new discord.Embed({
      title: `${message.author.username}'s avatar`,
      image: { url: avatarurl }
    })
  );
});
