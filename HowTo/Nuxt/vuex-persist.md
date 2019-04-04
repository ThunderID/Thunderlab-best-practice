1. Install 
```
npm install --save vuex-persist

```

2. Nuxt.config.jg
```
// Inside - nuxt.config.js
export default {
  plugins: [
    { src: '~/plugins/vuex-persist', ssr: false }
  ]
}
```

```
// ~/plugins/vuex-persist.js
import VuexPersistence from 'vuex-persist'

export default ({ store }) => {
  window.onNuxtReady(() => {
    new VuexPersistence({
    /* your options */
    }).plugin(store);
  });
}
```

3. Store/index.js
Use with mutations

```
import VuexPersistence from 'vuex-persist'
const vuexLocal = new VuexPersistence({
  storage: window.localStorage
})

const store = new Vuex.Store<State>({
  state: { ... },
  mutations: { ... },
  actions: { ... },
  plugins: [vuexLocal.plugin]
})
```