# Dataloader Sequelize

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

Batching, caching and simplification of Sequelize with facebook/dataloader

# How it works

dataloader-sequelize is designed to provide per-request caching/batching for sequelize lookups, most likely in a graphql environment

# API

## `createContext(sequelize, object options)`
* Should be called after all models and associations are defined
* `sequelize` a sequelize instance
* `options.max=500` the maximum number of simultaneous dataloaders to store in memory. The loaders are stored in an LRU cache

# Usage
```js
import {createContext, EXPECTED_OPTIONS_KEY} from 'dataloader-sequelize';

/* Per request */
const context = createContext(sequelize); // must not be called before all models and associations are defined
await User.findById(2, {[EXPECTED_OPTIONS_KEY]: context});
await User.findById(2, {[EXPECTED_OPTIONS_KEY]: context}); // Cached or batched, depending on timing
```

## Priming

Commonly you might have some sort of custom findAll requests that isn't going through the dataloader. To reuse the results from a call such as this in later findById calls you need to prime the cache:

```js
import {createContext, EXPECTED_OPTIONS_KEY} from 'dataloader-sequelize';
const context = createContext(sequelize);

const results = await User.findAll({where: {/* super complicated */}});
context.prime(results);

await User.findById(2, {[EXPECTED_OPTIONS_KEY]: context}); // Cached, if was in results
```

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟