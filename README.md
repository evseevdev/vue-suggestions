# Vue-suggestions
Vue компонент для плагина сервиса Подсказок DaData.ru

# Требования
- Vue.js `^2.3.0`

# Установка

## npm

```shell
$ npm install vue-suggestions
```

# Использование
```html
<template>
  <div>
    <VueSuggestions :model.sync="city" :placeholder="'Начните вводить'" :class="form-control" :options="suggestionOptions"></VueSuggestions>
  </div>
</template>

<script>
  import VueSuggestions from 'vue-suggestions';

  export default {
    data() {
      return {
        city: '',
        suggestionOptions: {
          token: 'abcd123',
          type: "ADDRESS",
          scrollOnFocus: false,
          triggerSelectOnBlur: false,
          triggerSelectOnEnter: false,
          addon: 'none',
        },
      }
    },
    components: { VueSuggestions }
  }
</script>