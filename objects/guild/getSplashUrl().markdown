```ts
commands.raw(
  'splash',
  async (message) => {
    let guild = await discord.getGuild();

    let inviteimagecode = guild.splash;
    //If you wonder what splash is, there is the option to set a custom invite image
    //once your server reached lvl 1, this displays that
    
    //CAREFUL!! guild.splash is not the image! It just gives you the ID or smth

    if (inviteimagecode) {
      //Checks if the guild has a splash
      let inviteimage = guild.getSplashUrl();
      //This is how you get the splash image Url

      await message.reply(
        new discord.Embed({
          title: `Splash for ${guild.name}. Splash code: ${inviteimagecode}`,
          image: { url: inviteimage }
        })
      );
    } else {
      await message.reply('This server has no splash thingy (BOOST!!!)');
    }
  }

);
