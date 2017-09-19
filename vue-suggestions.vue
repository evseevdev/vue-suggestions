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
      coordinates: {},
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
        value: '',
        coords: {
          latitude: '',
          longitude: ''
        },
      }
    },
    mounted() {
      this.value = this.model;
      this.initSuggestion();
    },
    watch: {

      'coords.latitude'() {
        this.$emit('update:coordinates', this.coords);
      },

      'coords.longitude'() {
        this.$emit('update:coordinates', this.coords);
      },

      value() {
        this.$emit('update:model', this.value);
      },

      model() {
        this.value = this.model;
      }

    },
    methods: {

      initSuggestion() {
        const options = Object.assign({}, this.options, { onSelect: this.onSelect });
        $(this.$el).suggestions(options);
      },

      onSelect(suggestion) {
        this.value = suggestion.value;
        this.coords.latitude = suggestion.data.geo_lat;
        this.coords.longitude = suggestion.data.geo_lon;
      }
    }
  };
</script>
