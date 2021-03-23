# Discoder
## _\*Create Discord for this coder_

📜 Discoder is a database service for coder that utilizes Discord.

📜 Use discord guild as database..

- You can easily prepare a database.
- It's interesting to see how the database works. 
- You can also monitor.


[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)   [![Build Status](https://travis-ci.org/KOU00000-github/discoder.svg?branch=main)](https://travis-ci.org/KOU00000-github/discoder.svg?branch=main)

## Features

- Corresponds to the new version of discord.
- Improve operation speed.

## Install
<details><summary> (1 ~ 2)When npm cannot be used</summary><div>

1. Make npm commands available
[install with node.js](https://nodejs.org/en/download/ "nodejs")
2. Move to the location you want to install.

format

`> cd <directory path>`

example

`> cd C:/Users/DISCORD/Desktop/project/`


</div></details>

3. and Execute the following command
```
> npm Install --save discoder
```

## Environment
 - need discord bot and its token

## How to use

### step1
Generate DB Object
```js
    //read this package
const cloud = require('discoder');
    //Generate DB Object
const DB = new cloud()
```
### step2
Database setting
<details><summary>if you need cryption</summary><div>

```js
//Turn on crypt
DB.encodOn();
//setkeys
DB.setKey("(32 alphanumeric characters)","(16 alphanumeric characters)");
```

</div></details>

Generate DB client
```js
//Generate client
const client = await DB.create("Your token is here",{
    server:"Your Server ID for database",
    name:"DataTable name"
},{} //<--- Value for the first time
);
```

### tep4
use database

- Usage
```js
    /**
     * Since it processes asynchronously, 
     * the program shold write in an asynchronous function.
     */
(async()=>{
    /**
     * write in here.
     */
})()
```
- Event
```js
//on client ready
client.on('ready',async ()=>{
    console.log('ready...');
        /**
         * The program that operates the database shold write in here.
         */
})

//on client's error
client.on('error',err=>{
    console.log(err.message);
});

        /**
         * Notify when data set is complete
         */
client.on('set',data=>{
    data = data[0];//main content (data[1] is this process's key)
    console.log(data.processTime);//Time it took to set
    console.log(data.setData);//Setted data
    
    //get client infomations by
    console.log(data.info);
    // OR //
    DB.info();
});
        
        /**
         * Notify when data get is complete
         */
client.on('get',data=>{
    var info = data[0]; //main content
    var key = data[1]; //this process's key
});

        /**
         * Notify once when nothing is written.
         */
client.once('writeEnd',async ()=>{
    console.log(await DB.get());
});
```
- Database operation
```js
        /**
         * Emphasis is placed on efficiency and safety.
         * The method that directly operates the DB is
         * Only set, get and create are available.
         */
         
//set
await DB.set("text")//set "text" on database
.then(async()=>{
    console.log(await DB.get())
    //stdout: "text"
}); 

//get
console.log(await DB.get())
```

## License

MIT

**Free Software, Hell Yeah!**
