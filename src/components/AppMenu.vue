<template>
  <div class="menu-container">
    <div class="grid-right reset-space">
      <div class="col reset-space">
        <div class="menu-wrapper">

          <menu-button v-on:windowToggle="windowToggle">
          </menu-button>

          <transition name="fade">
            <div class="menu-actions"
                  v-if="windowOpen">
                  <a href="#"
                     v-bind:class="['menu-item', viewActive === 'add' ? 'active' : '']"
                     ref="add"
                     v-on:click.prevent="emitButtonClick('add')">
                    Add
                    <ui-ripple-ink trigger="add"></ui-ripple-ink>
                  </a>
                  <a href="#"
                     v-bind:class="['menu-item', viewActive === 'manage' ? 'active' : '']"
                     ref="manage"
                     v-on:click.prevent="emitButtonClick('manage')">
                     Manage
                     <ui-ripple-ink trigger="manage"></ui-ripple-ink>
                  </a>
                  <a href="#"
                     ref="settings"
                     v-bind:class="['menu-item', viewActive === 'settings' ? 'active' : '']"
                     v-on:click.prevent="emitButtonClick('settings')">
                     Settings
                     <ui-ripple-ink trigger="settings"></ui-ripple-ink>
                  </a>
            </div>
          </transition>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MenuButton from './MenuButton.vue'

import { UiRippleInk } from 'keen-ui';

export default {
  components: {
    MenuButton,
    UiRippleInk
  },
  data () {
    return {
    }
  },
  methods: {
    emitButtonClick: function (id) {
      this.$emit('emitButtonClick', id)
    },
    windowToggle: function () {
      this.$emit('windowToggle')
    }
  },
  props: [
    'windowOpen', 'viewActive'
  ]
}
</script>