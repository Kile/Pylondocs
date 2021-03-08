```ts
commands.raw('banner', async function (message) {
  const guild = await discord.getGuild();
  const banner = guild.banner;

  // If you wonder what a banner is, there is the option to set a custom banner
  // once your server reached lvl 2 which is displayed on the right side of the server,
  // this displays the Id of that

  // CAREFUL!! guild.banner is not the image! It just gives you the ID or smth

  //Checks if the guild has a banner
  if (banner !== null) {
    //This is how you get the Banner image Url you can use
    const bannerUrl = guild.getBannerUrl();

    await message.reply(
      new discord.Embed({
        title: `Splash for ${guild.name}. Splash code: ${ banner }`,
        image: { url: bannerUrl }
      })
    );
  } else await message.reply('This server has no banner (BOOST!!!)');
});
```
