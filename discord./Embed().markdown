```ts
commands.raw('invite', async function (message) {
  let embed = new discord.Embed();
  embed.setTitle('Invite link');
  embed.setDescription(
    'Invite my cool bot [here](https://discord.com/oauth2/authorize?client_id=756206646396452975&scope=bot&permissions=1574431991)'
  );
  embed.setColor(0x1400ff);

  await message.reply(embed);
});
```
