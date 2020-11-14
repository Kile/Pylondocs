```ts
let channel = await discord.getChannel('THE_CHANNEL_ID_OF_THE_CHANNEL_WITH_THE_MESSAGE')

let message = await channel.getMessage('THE_ID_OF_THE_MESSAGE')

//Remember to use await
//In commands and some events you already define message. Example: async(message)=>
//This message is the text issuing the command/event. Of course you can name it as you wish
//but I would recommend message or msg to keep track
