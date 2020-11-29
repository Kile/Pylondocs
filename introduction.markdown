## Pylon SDK and TypeScript introduction

Hello there! Looks like you chose Pylon to programm your own discord bot, easily deployable with no traps or hidden costs. You have made the right choice :3

This page will give you a first overview of Pylon SDK and typscript for absolute beginners so you can start experimenting

First the basics:

  -No code will work outside an **async function** (exceptions but I will come to that later)
  
  -To save and publish a script you need to click on **script and publish**. If this action is not successfully made it deletes your last changes
  
## async functions
  
  What are **async functions**?
  
  There are three ways of creating an **async funtion**. One is making a command. You first need to define that you want a command: 
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

Next we use `async(message)=>{`. Remember when I said **async function**? Here you define it as **async function**, you will need to put this in every command,
every other way of starting to make Pylon do something. In the `()` I wrote `message`. You can call this anything but I would call it message
to keep track. `message` is a **discord message object**. It is the message you send to invoke this command

Now we start with the actual code inside the command. First I used `await`, you *can* not use it in this case but it is not good practice if you
don't use it. We now use the `message` object we just defined in the code. We tell Pylon to **reply** to that message. This doesn't mean discord reply feature,
only that Pylon sends a message in the same channel the command was used in. In the `()` you can now put what you want Pylon to send in response to the command
you use. **BUT REMEMBER**, it **must** be a string because you want to text. To make text a string use `''` around it as established before

Now all we have to do is close all `()` and `{}`.

Note: Remember to always close them and to close a string after you started it with a `'`. If you don't know where to close what, look at what you opened
first, this will be the thing you will want to close last. You mostly will use normal `()`, for now only worry about `{}` after the `=>` of an **async function**

*To be continued...*
