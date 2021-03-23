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

## How to use

```js
(async function(){
 
    const cloud = require('discloud');
    const DB = new cloud;
 
    /**
     * How to set when DB is generated
     * -It can also be set using DB.setting()
     */
    const DB = new cloud({
        encode:{//encode settings
            use:true,//encode = on
            key:{
                keyA:"(32 alphanumeric characters)",
                keyB:"(16 alphanumeric characters)"
            }
        },
        token:"Your token is here",
        server:"Your Server ID (This server id's server will be a database)"
    });
 
    /**
     * How to use encode
     */
    DB.encodOn();//Turn on encoding
    DB.setKey("(32 alphanumeric characters)","(16 alphanumeric characters)");//set key
 
    const client = await DB.create("Your token is here",{
        server:"Your Server ID (This server id's server will be a database)",
        //DB.setServer("ID");//You can also set this way
        name:"DataTable's name"
    },
    {}//The value to be set first when creating db
    );
    client.on('error',err=>{
        console.log(err.message);//throw client's error here
    })
    client.on('ready',async ()=>{//client ready
        console.log('ready...');
 
        /**
         * Emphasis is placed on efficiency and safety.
         * The method that directly operates the DB is
         * Only set, get and create are available.
         * Other methods to change settings (such as switching encryption)
         * There is.
         */
        await DB.set("text")//set data in database
        .then(async()=>{
            console.log(await DB.get())
            //text
        }); 
        /**
         * Notify when data set is complete
         */
        client.on('set',data=>{
            data = data[0];//main content (data[1] is this process's key)
            console.log(data.processTime);//Time it took to set
            console.log(data.setData);//Seted data
            console.log(data.info);// = DB.info()
        });
        client.on('get',data=>{
            var info = data[0];
            //main content
            var key = data[1];
            //this process's key
        });
        /**
         * Notify once when nothing is written.
         */
        client.once('writeEnd',async ()=>{
            console.log(await DB.get());
        });
 
        DB.info();
        //You can get Your DB's infomations
    });
})();
```

## License

MIT

**Free Software, Hell Yeah!**
