```ts
commands.raw(
  'splash',
  async function (message) {
    const guild = await discord.getGuild();

    const inviteimagecode = guild.splash;
    // If you wonder what splash is, there is the option to set a custom invite image
    // once your server reached lvl 1, this displays that
    
    // CAREFUL!! guild.splash is not the image! It just gives you the ID or smth

    // Checks if the guild has a splash
    if (inviteimagecode !== null) {
      // This is how you get the splash image Url
      const inviteimage = guild.getSplashUrl();

      await message.reply(
        new discord.Embed({
          title: `Splash for ${guild.name}. Splash code: ${ inviteimagecode }`,
          image: { url: inviteimage }
        })
      );
    } else await message.reply('This server has no splash thingy (BOOST!!!)');
  }
);
```
