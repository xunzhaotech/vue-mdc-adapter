<template>
<div :class="formFieldClasses" class="mdc-switch-wrapper">
  <div class="mdc-switch" ref=root 
    :class="{ 'mdc-switch--disabled': disabled }">
    <input ref="control" type="checkbox" :id="_uid" 
      class="mdc-switch__native-control" 
      @change="onChanged" :checked="checked" :disabled="disabled"/>
    <div class="mdc-switch__background">
      <div class="mdc-switch__knob"></div>
    </div>
  </div>
  <label :for="_uid" v-if="label">{{ label }}</label>
</div>
</template>

<script>

export default {
  name: 'mdc-switch',
  model: {
    prop: 'checked',
    event: 'change'
  },
  props: {
    'checked': Boolean,
    'label': String,
    'alignEnd': Boolean,
    'disabled': Boolean,
    'value': { type: String, default () { return 'on' } }
  },
  data () {
    return {
      formFieldClasses: {
        'mdc-form-field': this.label,
        'mdc-form-field--align-end': this.label && this.alignEnd
      }
    }
  },
  watch: {
    'disabled' (value) {
      this.foundation.setDisabled(value)
    }
  },
  computed: {
  },
  methods: {
    onChanged (event) {
      this.$emit('change', event.target.checked)
    }
  }
}
</script>
