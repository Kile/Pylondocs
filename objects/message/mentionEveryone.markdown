```ts
discord.on('MESSAGE_CREATE', async(message)=>{
  if (
    message.mentionEveryone &&
    !message.member?.roles.includes(
      'THE_ID_OF_THE_ROLE_WHO_IS_ALLOWED_TO_USE_@EVERYONE'
    )
    //If someone mentions everyone and doesn't have the role you specified they get banned
    //because noby likes to be @everyone'd by a troller
  ) {
    await message.member?.ban();
    //Bans the user
    await message.reply(
      'Banned ' + message.author.getTag() + ' for mentioning @everyone'
    );
  }
});
```
