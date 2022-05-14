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
