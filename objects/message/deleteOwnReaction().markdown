```ts
discord.on('MESSAGE_REACTION_ADD', async (reaction) => {
  const channel = await discord.getTextChannel(reaction.channelId);
  const message = await channel?.getMessage(reaction.messageId);
  //Steps to get a message object

  await message?.deleteOwnReaction(reaction.emoji.name!);
  //If Pylon reacted to a message somehwere you can now just react to that message
  //yourself and Pylon removes it's own reaction
});
