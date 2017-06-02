<template>
  <input type="text" v-model="value">
</template>

<script>
  import $ from 'jquery';
  import 'suggestions-jquery';

  export default {
    props: {
      model: {
        required: true
      },
      options: {
        type: Object,
        default: {
          type: 'ADDRESS',
          addon: 'none'
        }
      }
    },
    data() {
      return {
        value: ''
      }
    },
    mounted() {
      this.initSuggestion();
    },
    watch: {
      value() {
        this.$emit('update:model', this.value);
      },
    },
    methods: {

      initSuggestion() {
        const options = Object.assign({}, this.options, { onSelect: this.onSelect });
        $(this.$el).suggestions(options);
      },

      onSelect(suggestion) {
        this.value = suggestion.value;
      }

    }
  };
</script>