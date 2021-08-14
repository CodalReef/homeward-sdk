#  Homeland

>  A laughably simple, cross-platform library for saving deep links to your home screen.  Works with Expo Managed Workflow, no linking necessary =)

This library works by re-directing users to a web-browser where they can then save a deep link to their home screen.

This is a technique used by several popular apps and documented on Stack Overflow here:  https://stackoverflow.com/questions/28042152/link-to-safari-add-to-home-screen-from-inside-app

*Please see Pitch / Anti-Pitch, Disclaimer, and License prior to using.*

##  Installation

Npm
`npm i --save https://github....`

Yarn
`yarn add --save https://github....`

##  Usage

Pass a JSON object to the `saveToHome` function to re-direct the user to a web-browser.

Upon re-direction the user is prompted with instructions for saving the link to the home screen.

Currently, the style of the icon is simply a single letter and a background color.  (See Roadmap for )

### Example

```typescript
import { saveToHome } from 'homeland';

saveToHome({
  name: "Calendar",
  letter: "C",
  backgroundColor: "e33681",
  themeColor: "e33681",
  link: Linking.makeUrl(),
  payload: { page: "calendar", params: { day: "today" } }
)
```

In this example, we've created an icon with a letter "C" in the center and a pinkish-red background.

When tapped, user will be directed to the app using the supplied payload.  Presumably, they would be navigated to the "Calendar" section of the app showing data relevant to "today".


##  API
```
saveToHome({
  name: <Shortcut Name>,
  letter: <Shortcut Letter>,
  backgroundColor: <>,
  themeColor: "888888",
  link: "exp://172.20.10.2:19000/--/test",
  payload: <>
}: SaveToHomeParams)
```

Params
```
interface SaveToHomeParams {
  name: string;
  description?: string;
  letter: string;
  link: string;
  backgroundColor: string;
  themeColor: string;
  payload?: any;
  devServer?: string;
  prodServer?: string;
}
```

## Pitch / Anti-Pitch

In the future, it would be preferable to skip the browser and use native libraries instead.

While such solutions *are* available now, there are several concerns which I've documeted in our Dev.to article here:  Article Link


##  Roadmap

It would be ideal to skip the browser altogether and use native libraries as I discuss here:  DEV LINK.

So while this library remains relevant, I'd like to focus on:

-  Extensibility
--  Modularize the renderer to use a user-specified component.
--  Support "Plugins" to dynamically generate various icon types.
--  Remove theh "dev" vs. "prod" distinction and inject that differentiation with a Plugin as needed.
--  Generally, make this library "Pluggable" as I discuss here:  

###  Disclaimer

The public debug end-point, currently located at https://www.oranda.io/link, is for debugging purposes only.  It is provided AS IS, without warranty, subject to undocumented change, and should not be used for  production, confidential, or otherwise sensitive payloads.

>  We are currently in the process of releasing the server code so you can deploy your own re-direct server.

###  License

Both this codebase and the public debug end-point, currently located at https://www.oranda.io/link), are licensed under the (MIT License)[License Link].

##  Contact

Dev.to:  
Email:  codalreef@gmail.com