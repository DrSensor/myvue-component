<template>
  <div>
    <myvue-component
      :hello="hello"
      @click="clicked"
    >
      <span>This is default slot</span>
    </myvue-component>
  </div>
</template>

<script>
/**@see https://github.com/storybooks/storybook/tree/master/addons/knobs#available-knobs */
import { text } from '@storybook/addon-knobs/vue'

export default {
  components: {
    MyvueComponent: () => import('@/MyvueComponent')
  },
  data () {
    return {
      hello: text('hello text', 'Hello World!!!')
    }
  },
  methods: {
    action (label, data) {
      this.$emit('action', label, data)
    },
    clicked (helloText) {
      this.action('button-click', helloText)
    }
  }
}
</script>
