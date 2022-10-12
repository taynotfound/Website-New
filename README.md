<h1 align="center">Tayron Site</h1>

[![Preview](https://i.imgur.com/OxrX3hE.png)](https://i.imgur.com/OxrX3hE.png)
<br />

## Basics
This is a [Next.js](https://nextjs.org/) project bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app).
First, run the development server:

```bash
npm run dev
# or
yarn dev
```

To deploy and start the server run:

```bash
npm run build
npm run start
# or
yarn build
yarn start
```

## 1. Bio
You can edit your bio in the [`pages/index.jsx`](https://github.com/Luna-devv/luna-site/blob/main/config.js#L44). <br />
Note that you shouldn't edit anything outside of the div showed bellow because this could break the sites design.
```jsx
<div className={style.readme}>
    { /* Put your bio here */ }
</div>
```

## 2. Cards
Cards are here to display your various projects. You can set these in the [`config.js`](https://github.com/Luna-devv/luna-site/blob/main/config.js) in the [cards Array](https://github.com/Luna-devv/luna-site/blob/main/config.js#L26). <br />
Here is an example how the **each** card could look like:
```js
{
    name: "discord-botlist.eu",
    icon: "https://cdn.discord-botlist.eu/pictures/logo.png",
    description: "We give you the ability to apply and give your bot a page on our site.",
    url: "https://discord-botlist.eu",
    position: "Moderator",
    bot: 0
}
```
With the `bot` variable you can show off if it's a discord bot or not. `1` is a normal bot and `2` would be a verified discord bot. <br />
Please note that `cards` should **not** be an [Object](https://www.w3schools.com/js/js_objects.asp)(!), it needs to be an [Array](https://www.w3schools.com/js/js_arrays.asp) with the structure __in it__ showed above.


## 3a. Use static data
If you don't want to use an API, just go to the [`config.js`](https://github.com/Luna-devv/luna-site/blob/main/config.js) and set both [`api.url`]((https://github.com/Luna-devv/luna-site/blob/main/config.js#L3)) and [`api.path`]((https://github.com/Luna-devv/luna-site/blob/main/config.js#L4)) to [`null`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/null). <br />
 In the next step enter your user data in the [user Object](https://github.com/Luna-devv/luna-site/blob/main/config.js#L6). <br />

Here is an example how the config.js could look like at this point:
```js
module.exports = {
    api: {
        url: null,
        path: null
    },
    user: {
        id: "821472922140803112",
        username: "Lunish",
        discriminator: "8888",
        nickname: "Luna",
        nickavatar: "https://cdn.waya.one/r/luna_lone1.gif",
        status: {
            state: {
                text: "dnd",
                color: "#ED4245"
            },
            emote: "https://cdn.discordapp.com/emojis/682858108862726191.gif?size=2048",
            text: "waya.one • Stressed out"
        },
        activities: [],
        createdTimestamp: 1615924806867,
        avatar: "https://cdn.waya.one/r/luna_lone1.gif",
        banner: "https://cdn.waya.one/r/sunset.gif",
        accentColor: "#ce3760"
    }
}

```

## 3b. Use an API
The best way to use this website is using an internal-API. <br />
You can set the API URL in the [`config.js`](https://github.com/Luna-devv/luna-site/blob/main/config.js#L3), please note that this should be only the domain name with the protocol like `https://api.waya.one`. The URL should __**not**__ have the path in it like `https://api.waya.one/` or `https://api.waya.one/luna`! <br />

In the [`config.js`](https://github.com/Luna-devv/luna-site/blob/main/config.js#L4) you also need to set the PATH after the domain name. If you want to use the root domain just paste a `/` in there, otherwise put the full path in there for example `/luna`. At the end the URL plus the PATH __together__ should look like `[domain][path]` (eg.: `https://waya.one/luna`). <br />

The API needs to acknowledge the request with a [http `200`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200) status code in order to work. I personally recommend you also to fill in the [user Object](https://github.com/Luna-devv/luna-site/blob/main/README.md#3a-use-static-data) in case that the API should not respond. <br />
A code example/template for the API can be found in the [gist here](https://gist.github.com/Luna-devv/5793ced1319f4fc3a6c713bfb89f9854). <br />

The API should respond with a JSON structure that looks like this: 
```json
{
    "status": 200,
    "message": "OK",
    "content": {
        "id": "821472922140803112",
        "username": "Lunish",
        "discriminator": "8888",
        "nickname": "Luna",
        "nickavatar": "https://cdn.discordapp.com/avatars/821472922140803112/a_5225c26456cd6d1d03b5f6af645d2488.gif?size=2048",
        "status": {
            "state": {
                "text": "dnd",
                "color": "#ED4245"
            },
            "emote": "https://cdn.discordapp.com/emojis/682858108862726191.gif?size=2048",
            "text": "waya.one • Stressed out"
        },
        "activities": [
            {
                "applicationId": "782685898163617802",
                "name": "Code",
                "url": null,
                "details": "Editing Luna site",
                "state": "Work on README.md:44:625",
                "createdTimestamp": 1643993478165,
                "timestamps": {
                    "start": 1643989464309,
                    "end": null
                },
                "assets": {
                    "large": {
                        "text": "Editing a MARKDOWN file",
                        "image": "https://cdn.discordapp.com/app-assets/782685898163617802/810647037598760991.png"
                    },
                    "small": {
                        "text": "Visual Studio Code - Insiders",
                        "image": "https://cdn.discordapp.com/app-assets/782685898163617802/810652286233083974.png"
                    }
                }
            }
        ],
        "createdTimestamp": 1615924806867,
        "avatar": "https://cdn.discordapp.com/avatars/821472922140803112/a_5225c26456cd6d1d03b5f6af645d2488.gif?size=2048",
        "banner": "https://cdn.discordapp.com/banners/821472922140803112/a_bb8eb557242c1923d82d86cef14bcc4a.gif?size=600",
        "accentColor": "#ffff"
    }
}
```

## 4. Header
The header is displayed on every page. It's here to display informations that could be useful everywhere like Icon, name and varius links such as Discord, GitHub and Twitter. To configure this data head over to the [`config.js`](https://github.com/Luna-devv/luna-site/blob/main/config.js#L57) once again and go to the `header` object. <br />

The object should look like this at the end:
```js
header: {
    icon: `https://cdn.waya.one/r/luna_lone1.gif`,
    name: `Luna Seemann`,
    buttons: {
        Discord: `/go/discord`,
        GitHub: `/go/github`,
        Twitter: `/go/twitter`
    }
}
```

## 5. Meta tags
Last but not least the meta tags. This are important if other websites like Discord, Twitter or Slack should show informations about your website, in the picture bellow you can see an example how it could look like in Discord.
<img src='https://cdn.waya.one/r/1645794994.png' style='border-radius: 0.4rem; max-height: 8rem;' /> <br />

However, open the [`config.js`](https://github.com/Luna-devv/luna-site/blob/main/config.js#L66) for the last time and edit the `metadata` object.
Please note that the `keywords` value needs to be an [Array](https://www.w3schools.com/js/js_arrays.asp) and the `color` value a valid [hex color](https://htmlcolorcodes.com/color-picker/)! <br />
This is how it could look like:
```js
metadata: {
    title: `Luna - Software Engineer and LGBTQ+ Activist`,
    description: `Heyia, I'm Luna and I was born 14 years ago and live in Austria.`,
    image: `https://avatars.githubusercontent.com/u/71079641?v=4`,
    domainName: `waya.one`,
    color: `#f19bec`,
    keywords: [
        'Luna',
        'Lunish',
        'Lunish#8888',
        'waya bot',
        'waya',
        'waya.one',
        'discord waya',
        ],
    }
```

## Support
If you need help don't hesitate to [join our discord](https://waya.one/go/discord) and ask for help.
