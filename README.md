## warframe-patchlogs
[![npm](https://img.shields.io/npm/v/warframe-patchlogs.svg)](https://npmjs.org/warframe-patchlogs)

[![Supported by Warframe Community Developers](https://warframestat.us/wfcd.png)](https://github.com/WFCD "Supported by Warframe Community Developers")

<br>

All warframe patchlogs parsed to more usable JSON. Also lets you find all
patchlogs for a specific item. This package has primarily been built for
[warframe-items](https://github.com/nexus-devs/warframe-items), so opinionated
decisions are based on the needs of that repository. If you're looking for
patchlogs on *all* items, you can find pre-compiled files there too.

<br>

### Installation
```
npm install warframe-items
```

<br>

### Usage
```js
const Patchlogs = require('warframe-patchlogs')
const patchlogs = new Patchlogs(options)

// .. inside async function
await patchlogs.setup // It'll fetch everything at runtime.
for (let post of patchlogs.posts) {
  console.log(post) // Have your terminal flooded with patch notes.
}
```
You'll be able to retrieve all posts via `patchlogs.posts`. If you need patchlogs
for a specific item, use `patchlogs.getItemChanges({ name: 'itemname', type: 'Warframe|Sentinel|etc' })`.
If the item type is `'Warframe'` and the name includes `'Prime'`,
then we'll look for changes in the default variants of the item too.

<br>

### Log Format
Log objects inside `patchlogs.posts` look like this:
```js
{
  name: 'Beasts of the Sanctuary: Hotfix 22.20.6',
  url: 'https://forums.warframe.com/topic/960140-beasts-of-the-sanctuary-hotfix-22206/',
  date: '2018-05-24T22:00:50Z',
  description: 'The Orokin Decoration costs/refunds mentioned in Hotfix 22.20.3 are close to being complete. The plan is to cut the Orokin Decoration Oxium costs in half and refund the excess back to the Clan Vault. We are also removing the Orokin Cell costs on the respective Orokin Decorations and refunding those to the Clan Vault as well. Already completed Decorations will not be destroyed when these changes go live. Stay tuned!',
  additions: '',
  changes: '',
  fixes: 'Fixed the game submitting certain types of bug reports immediately instead of saving them for after you quit.\nDisabled some cache-corruption checks that were triggering and preventing updates; we will work on making these automatically repair the cache instead.\nFixed inability to deploy Extractors using Navigation at a Relay.\nFixed a variety of bugs caused by using Transference while going through Sanctuary Onslaught Conduit (namely not being able to do anything or use Transference while controlling Operator).\nFixed Dojo Pigment ‘Contribute’ button being automatically selected when the contribute screen appears when using a controller.\nFixed no on-screen keyboard appearing when changing Dojo room message when using a controller. \nFixed script error when displaying mission countdown in Ukrainian.\nFixed a script error related to Articulas.',
  type: 'Hotfix' }
}
```

<br>

### Options
| Option        | Default       | Description   |
|:------------- |:------------- |:------------- |
| pages | `null` | Number of forum pages to look for posts in. Default fetches ALL posts, which is **not recommended** as it downloads around 200MB of data. We start counting at `1`.

<br>

### License
[MIT](/LICENSE)
