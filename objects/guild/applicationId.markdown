```ts
commands.raw('applicationId', async(message)=>{
let guild = await discord.getGuild();

await message.reply(guild.applicationId ?? 'No application Id');
//The ?? lets Pylon reply an other thing if, in this case, guild.vanityUrlCode doesn't exist

}
