<template lang="pug">
  .loading-wrapper.text-center.py-5
    b-spinner.spinner(label="Loading..." :type="type" :variant="variant")
    h1.my-5 Loading...
</template>
<script>
export default {
  name: 'Loading',
  props: {
    variant: {
      type: String,
      required: false,
      default: 'info',
      validator: value => {
        return (
          [
            'primary',
            'secondary',
            'danger',
            'warning',
            'success',
            'info',
            'light',
            'dark'
          ].indexOf(value) !== -1
        )
      }
    },
    type: {
      required: false,
      type: String,
      default: 'border',
      validator: value => {
        return ['border', 'grow'].indexOf(value) !== -1
      }
    }
  }
}
</script>
<style lang="stylus">
.spinner-wrapper
    .spinner
        width 4rem
        height 4rem
</style>
