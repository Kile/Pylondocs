```ts
commands.raw('avatar', async function (message) {
  const user = await discord.getUser(message.author.id);
  //You can insert any other ID here, even from people not on the guild
  const avatarurl = await user?.getAvatarUrl();

  await message.reply(
    new discord.Embed({
      title: `${ message.author.username }'s avatar`,
      image: { url: avatarurl }
    })
  );
});
```
