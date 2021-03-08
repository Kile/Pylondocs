## Pylon SDK and TypeScript introduction

Hello there! Looks like you chose Pylon to programm your own discord bot, easily deployable with no traps or hidden costs. You have made the right choice :3

This page will give you a first overview of Pylon SDK and typscript for absolute beginners so you can start experimenting

First the basics:

  - No code will work outside an [**async function**](https://github.com/Kile/Pylondocs/blob/main/introduction.markdown#async-functions) (exceptions but I will come to that later)
  
  - To save and publish a script you need to click on **script and publish**. If this action is not successfully made it deletes your last changes
  
## async functions
  
  What are **async functions**?
  
  **async functions** are the things you will use to make Pylon do something in response to either:
  
  \- a command
  
  \- an event
  
  \- a sceduled task
  
  If you try to make Pylon do something outside of an **async function** it will throw an error. There are ways to put code outside these three groups but I will come back to that later
  
# Commands
  
You first need to define that you want a command: 
```ts
const commands = new discord.command.CommandGroup({
  defaultPrefix: '!'
});
```
Great! You are all set to build your first command! You do so by using `.raw()` for a simple command, there are other options.
Lets look at how your first command would look:

```ts
commands.raw('test', async (message) => {
  await message.reply(
    'Test complete! (This command does not actually do anything)'
  );
});

```
Lets break down what exactly we are doing there. `''` means something is a **string**. A **string** is basically programmer language for normal
text. What **string** you use at the start depends on what you want your command to be. This command is called by typing `!test`.

Next we use `async(message)=>{`. Remember when I said [**async function**](https://github.com/Kile/Pylondocs/blob/main/introduction.markdown#async-functions)? Here you define it as [**async function**](https://github.com/Kile/Pylondocs/blob/main/introduction.markdown#async-functions), you will need to put this in every command, every other way of starting to make Pylon do something. In the `()` I wrote `message`. You can call this anything but I would call it message to keep track. `message` is a **discord message object**. It is the message you send to invoke this command

Now we start with the actual code inside the command. First I used `await`, you *can* not use it in this case but it is not good practice if you
don't use it. We now use the `message` object we just defined in the code. We tell Pylon to **reply** to that message. This doesn't mean discord reply feature,
only that Pylon sends a message in the same channel the command was used in. In the `()` you can now put what you want Pylon to send in response to the command
you use. **BUT REMEMBER**, it **must** be a string because you want to send a text. To make text a string use `''` around it as established before

Now all we have to do is close all `()` and `{}`.

Note: Remember to always close them and to close a string after you started it with a `'`. If you don't know where to close what, look at what you opened
first, this will be the thing you will want to close last. You mostly will use normal `()`, for now only worry about `{}` after the `=>` of an [**async function**](https://github.com/Kile/Pylondocs/blob/main/introduction.markdown#async-functions)

# Events

There are a lot of differnt **events** you can make Pylon react to but the most common one is **MESSAGE_CREATE**. This means your code is triggered whenever a message is created in your server. Let's take a look at an easy script for that:

```ts
discord.on(discord.Event.MESSAGE_CREATE, async (message) => {
  if (message.content == 'Hello') {
    await message.reply('Hello!');
  }
});
```
Time to analize what we do there: first, the method we use to look for events is `discord.on`. After the `(` we define the event to look for. You can either tell Pylon that with a string e.g. `'MESSAGE_CREATE'` or you use the cleaner (my opinion) way `discord.Event.MESSAGE_CREATE`. Now you see the similarity to the command, we again use `async (message) => {`.

Since we don't want Pylon to respond to *every* message we build in an **if check**.You will use **if checks** a lot in any programming language you coma across. They work as follows:
```ts
if (something) {
  do another thing
}
```
In this case you check if the **message content** `==` (that means equals exactly) the **string** (text) 'Hello'. If that is the case we do what we did before with the command, let Pylon **reply** with 'Hello!'. **REMEMBER** that this is case sensitive, so Pylon won't trigger uf you say 'hElLo'.

# Tasks

With task you can scedule when Pylon does what, without a requirement like `MESSAGE_CREATE` having to be fulfilled to be activated. This is a Pylon SDK specific thing meaning nothing normal TypeScript can do. It also means you start it with `pylon.`. Here is an example of that:

```ts
pylon.tasks.cron('Hello', '0 0 0/30 * * * * *', async () => {
  let guild = await discord.getGuild()
  let channel = await guild.getTextChannel('765969331343327304')
  
  await channel?.sendMessage('When:tm:')
})
```

Let's break this down: first we use something new, `pylon.`. Things that start with this are Pylon exclusive and you can't find them anywhere else. This scedules a Pylon cron task, meaning an event that us fired every x minutes/days/weeks/months etc. You first define what the cron tasks name is (It isn't actually important at all and doesn't impact what you're doing in any way). How you specify when a cron is gonna fire/in what intervall:

Look at [this](https://docs.oracle.com/cd/E12058_01/doc/doc.1014/e12030/cron_expressions.htm)

Then we are making it an [**asnyc function**](https://github.com/Kile/Pylondocs/blob/main/introduction.markdown#async-functions) again, this time nothing in the brackets because we have no object that activated the function like a `message` object or some other objects you will see further down the line. Then we define our `guild` object (=server) and with that object we can get a `channel` object by putting it's ID in the brackets. Having this we can use `sendMessage` on it sending the specifed message to the specified channel. This happens every 30 minutes in this case. 

Note: You can only have up to 5 cron tasks in your script. Consider putting multiple things in one cron if they should happen at the same interval. 
Additional Note: You can't make Pylon send messages in lower intervalls than 5 minutes, check if you try to do that when your code does not work.

*To be continued...*
