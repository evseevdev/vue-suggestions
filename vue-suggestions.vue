<template>
  <input type="text" v-model="value">
</template>

<script>
  import jQuery from 'jquery';
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
      coords: {
        handler() {
          this.$emit('update:coordinates', this.coords);
        },
        deep: true
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
        jQuery(this.$el).suggestions(options);
      },

      onSelect(suggestion) {
        this.value = suggestion.value;
        const { geo_lat, geo_lon } = suggestion.data;
        this.coords.latitude = geo_lat;
        this.coords.longitude = geo_lon;
      }
    }
  };
</script>
