```ts
commands.raw('owner', async function (message) {
  const guild = await discord.getGuild();

  const ownerid = guild.ownerId;

  await message.reply({
    content: `**Guild owner:** <@${ownerid}>`,
    allowedMentions: {}
  });
  // allowedMentions has the useful feature of not pinging the owner even though
  // mentioning them. This way users can click on the owner's profile but the
  // command doesn't ping the owner all the time
});
```
