<template>
  <li role="separator" class="mdc-list-divider" :class="classes"></li>
</template>

<script>
export default {
  name: 'mdc-list-divider',
  props: {
    'inset': Boolean
  },
  data () {
    return {
      classes: {
        'mdc-list-divider--inset': this.inset
      }
    }
  }
}
</script>
