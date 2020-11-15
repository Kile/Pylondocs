```ts
commands.raw('embify', async (message) => {
  if (message.attachments[0] && !message.attachments[1]) {
    //This makes sure there is only one attachment
    await message.reply(
      new discord.Embed({
        image: { url: message.attachments[0].url },
        color: 0x1400ff,
        footer: { text: `Requested by ${message.author.getTag()}` }
      })
    );
  } else {
    await message.reply(
      'You need to attach one (not more) images to this message to work'
    );
    //In case there are too many or less attachments it will reply this
  }
});
```
