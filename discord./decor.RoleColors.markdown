```ts
commands.raw('colors', async function (message) {
  const blue = discord.decor.RoleColors.BLUE;
  const red = discord.decor.RoleColors.RED;
  const green = discord.decor.RoleColors.GREEN;

  await message.reply(`__**Discord default role colors numeretical representation**__
Blue: ${blue}
Red: ${red}
Green: ${green}`);

  // Honestly I don't know what this would be useful for, but now you know it exists
});
