# Vue-suggestions
Vue компонент для плагина сервиса Подсказок DaData.ru

# Требования
- Vue.js `^2.3.0`

# Установка

## npm

```shell
$ npm install --save vue-suggestions
```

## yarn

```shell
$ yarn add vue-suggestions
```

# Использование
```html
<template>
  <div>
    <VueSuggestions
        :model.sync="city"
        :coordinates.sync="coordinates"
        :placeholder="'Начните вводить'"
        :class="'form-control'"
        :options="suggestionOptions">
    </VueSuggestions>
  </div>
</template>

<script>
  import VueSuggestions from 'vue-suggestions';

  export default {
    data() {
      return {
        city: '',
        coordinates: {
          latitude: '',
          longitude: ''
        },
        suggestionOptions: {
          // @see https://confluence.hflabs.ru/pages/viewpage.action?pageId=207454318
          token: 'abcd123',
          type: "ADDRESS",
          scrollOnFocus: false,
          triggerSelectOnBlur: false,
          triggerSelectOnEnter: false,
          addon: 'none',
          // @see https://confluence.hflabs.ru/pages/viewpage.action?pageId=207454320
          onSelect (suggestion) {
            
          }
        },
      }
    },
    components: { VueSuggestions }
  }
</script>
