<template>
  <a :class="['btn', variant, shadow, disable, iconSize, bgColor]">
    <span :class="['material-icons', hasStartIcon ? 'icon-left' : '']" v-if="hasStartIcon">{{ startIcon }}</span>
    <slot>Default</slot>
    <span :class="['material-icons', hasEndIcon ? 'icon-right' : '']" v-if="hasEndIcon">{{ endIcon }}</span>
  </a>
</template>

<script>
export default {
  name: 'Button',
  props: {
    variant: {
      type: String,
      default: 'default'
    },
    disableShadow: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    },
    startIcon: {
      type: String,
      default: ''
    },
    endIcon: {
      type: String,
      default: ''
    },
    size: {
      type: String,
      default: 'md'
    },
    color: {
      type: String,
      default: ''
    }
  },
  computed: {
    shadow() {
      return this.disableShadow ? '' : 'shadow';
    },
    type() {
      return ['outline', 'text', 'default'].includes(this.variant) ? this.variant : 'default';
    },
    disable() {
      return this.disabled ? 'disabled' : '';
    },
    hasStartIcon() {
      return this.startIcon.length && 1;
    },
    hasEndIcon() {
      return this.endIcon.length && 1;
    },
    iconSize() {
      return ['sm', 'md', 'lg'].includes(this.size) ? this.size : 'md';
    },
    bgColor() {
      return ['default', 'primary', 'secondary', 'danger'].includes(this.color) && this.variant === 'default' ? `bg-${this.color}` : '';
    }
  }
};
</script>

<style scoped lang="scss">
.btn {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-content: center;
  align-items: center;
  text-decoration: none;
  height: 20px;
  font-family: "Noto Sans JP", sans-serif;
  font-style: normal;
  font-weight: 500;
  font-size: 14px;
  line-height: 20px;
  text-align: center;
  border-radius: 6px;
  cursor: pointer;
  user-select: none;
  &.shadow {
    box-shadow: 0px 2px 3px rgba(51, 51, 51, 0.2);
  }
  &.default {
    background: #E0E0E0;
    color: #3F3F3F;
    &:hover, &:focus {
      background: #AEAEAE;
    }
  }
  &.outline {
    background: #FFFFFF;
    color: #3D5AFE;
    border: 1px solid #3D5AFE;
    &:hover, &:focus {
      background: rgba(41, 98, 255, 0.1);
    }
  }
  &.text {
    background: #FFFFFF;
    color: #3D5AFE;
    &:hover, &:focus {
      background: rgba(41, 98, 255, 0.1);
    }
    &.disabled {
      background: #FFFFFF !important;      
    }
  }
  &.disabled {
    background: #E0E0E0;
    color: #9E9E9E !important;
    pointer-events: none;
    box-shadow: 0 0 0 0 transparent;
    &.outline {
      border: none;
    }
    &.text {
      background: #ffffff;
    }
  }
  &.sm {
    padding: 6px 12px;
  }
  &.md {
    padding: 8px 16px;
  }
  &.lg {
    padding: 11px 22px;
  }
  &.bg-default {
    background: #E0E0E0;
    color: #3F3F3F;
    &:hover, &:focus {
      background: #AEAEAE;
    }
  }
  &.bg-primary {
    background: #2962FF;
    color: #FFFFFF;
    &:hover, &:focus {
      background: #0039CB;
    }
  }
  &.bg-secondary {
    background: #455A64;
    color: #FFFFFF;
    &:hover, &:focus {
      background: #1C313A;
    }
  }
  &.bg-danger {
    background: #D32F2F;
    color: #FFFFFF;
    &:hover, &:focus {
      background: #9A0007;
    }
  }
}
.icon-left {
  margin-right: 10px;
}
.icon-right {
  margin-left: 10px;
}
.material-icons {
  font-size: 14px;
}
</style>
