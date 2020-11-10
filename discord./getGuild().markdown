commands.raw('servername', async(message)=>{
  let guild = await discord.getGuild();
  //Gives you a guild object you can get a lot of information from
  //and you can also modify it with .edit()

  await message.reply(`Guild name: ` + guild.name)
})
