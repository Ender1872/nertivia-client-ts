<template>
  <button
    class="button"
    type="submit"
    :class="{
      warn: !disabled && warn,
      valid: !disabled && valid,
      disabled
    }"
    @click="$emit('click')"
  >
    <span v-if="icon && iconPos !== 'right'" class="material-icons icon left">{{
      icon
    }}</span>
    {{ name }}
    <span
      v-if="icon && iconPos === 'right'"
      class="material-icons icon right"
      >{{ icon }}</span
    >
  </button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class CustomInput extends Vue {
  focused = false;
  @Prop() private name!: string;
  @Prop() private warn!: boolean;
  @Prop() private disabled!: boolean;
  @Prop() private valid!: boolean;
  @Prop() private icon!: string;
  @Prop() private iconPos!: string;
}
</script>

<style lang="scss" scoped>
.button {
  display: flex;
  align-items: center;
  align-content: center;
  justify-content: center;
  margin: 4px;
  border-radius: 6px;
  padding: 8px;
  font-size: 14px;
  border: none;
  cursor: pointer;
  user-select: none;
  background: none;
  outline: none;
  transition: 0.2s;
  color: rgba(255, 255, 255, 0.7);
  background: rgba(255, 255, 255, 0.05);

  &:hover {
    background: var(--primary-color);
    color: white;
    .icon {
      color: white;
    }
  }
  &.warn:hover {
    background: var(--alert-color);
  }
  &.valid:hover {
    background: var(--success-color);
  }
}
.icon {
  color: var(--primary-color);
  transition: 0.2s;
  &.left {
    margin-right: 5px;
  }
  &.right {
    margin-left: 5px;
  }
}
.warn .icon {
  color: var(--alert-color);
}
.valid .icon {
  color: var(--success-color);
}
</style>
