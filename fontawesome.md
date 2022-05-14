# Setup FontAwesome with Nuxt 3
### Install Dependecies
```bash
# Current: @fortawesome/vue-fontawesome@^3.0.0-5
npm i --save @fortawesome/vue-fontawesome@prerelease

npm i --save @fortawesome/fontawesome-svg-core
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/free-regular-svg-icons
```
### Nuxt 3 Plugin
 - Create nuxt plugin `/plugins/fontawesome.client.js`
 
```js
// `/plugins/fontawesome.client.js`
import { library } from "@fortawesome/fontawesome-svg-core";
import { faPhone } from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

library.add(faPhone);

export default defineNuxtPlugin((nuxtApp) => {
  nuxtApp.vueApp.component("font-awesome-icon", FontAwesomeIcon)
})
```
# Setup FontAwesome with Vue 3

### Install Dependecies

```bash
# Current: @fortawesome/vue-fontawesome@^3.0.0-5
npm i --save @fortawesome/vue-fontawesome@prerelease

npm i --save @fortawesome/fontawesome-svg-core
npm i --save @fortawesome/free-solid-svg-icons
npm i --save @fortawesome/free-regular-svg-icons
```

### Vue 3 Plugin
 
```js
// `/src/main.js`
import { createApp } from 'vue'
import App from './App.vue'

import { library } from '@fortawesome/fontawesome-svg-core'
import { faMagnifyingGlass as fasMG } from '@fortawesome/free-solid-svg-icons'
import { faMagnifyingGlass as farMG } from '@fortawesome/free-regular-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(fasMG)
library.add(farMG)

const app = createApp(App)
app.component('icon', FontAwesomeIcon)
app.mount('#app')
```
