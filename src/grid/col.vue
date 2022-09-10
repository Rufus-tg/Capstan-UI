<template>
  <div class="g-col" :class="colClass" :style="colStyle">
    <slot></slot>
  </div>
</template>
<script>
const validator = (value) => {
  const keys = Object.keys(value);
  let isValid = true;
  keys.forEach((el) => {
    if (!["span", "offset"].includes(el)) {
      isValid = false;
    }
  });
  return isValid;
};
export default {
  props: {
    span: {
      //传进来的值有可能是字符串
      type: [String, Number],
    },
    offset: {
      //传进来的值有可能是字符串
      type: [String, Number],
    },
    // 接收传入的样式变量
    ipad: {
      type: Object,
      validator,
    },
    narrowPc: {
      type: Object,
      validator,
    },
    pc: {
      type: Object,
      validator,
    },
    widePc: {
      type: Object,
      validator,
    },
  },
  data() {
    return {
      gutter: 0,
    };
  },
  methods: {
      creatClasses(obj, str='') {
          if (!obj) return [];
          const arr = [];
          if (obj.span) {arr.push(`col-${str}${obj.span}`)};
          if (obj.offset) {arr.push(`offset-${str}${obj.offset}`)};
          return arr;
      }
  },
  computed: {
    colClass() {
      const { span, offset, ipad, narrowPc, pc, widePc, creatClasses} = this;
      return [
        span && `col-${span}`,
        offset && `offset-${offset}`,
        // 根据传入的样式变量给dom动态添加对应的class名
        ...creatClasses(ipad, 'ipad-'),
        ...creatClasses(narrowPc, 'narrow-pc-'),
        ...creatClasses(pc, 'pc-'),
        ...creatClasses(widePc, 'wide-pc-'),
      ];
    },
    colStyle() {
      return {
          paddingLeft: this.gutter / 2 + 'px',
          paddingRight: this.gutter / 2 + 'px',
      };
    },
  },
};
</script>
<style scoped lang='scss'>
.g-col {
  height: 50px;
//   // background: grey;
  border: 1px solid black;
  width: 50%;
  // .col .col-1 设置col的宽度，24等分
  $class: col-;
  @for $n from 1 through 24 {
    &.#{$class}#{$n} {
      width: ($n / 24) * 100%;
    }
  }
  $class: offset-;
  @for $n from 1 through 24 {
    &.#{$class}#{$n} {
      margin-left: ($n / 24) * 100%;
    }
  }
  // 设置不同屏幕尺寸下，相关的样式生效
  @media (min-width: 577px) {
    $class: col-ipad-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        width: ($n / 24) * 100%;
      }
    }
    $class: offset-ipad-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        margin-left: ($n / 24) * 100%;
      }
    }
  }
  @media (min-width: 769px) {
    $class: col-narrow-pc-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        width: ($n / 24) * 100%;
      }
    }
    $class: offset-narrow-pc-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        margin-left: ($n / 24) * 100%;
      }
    }
  }
  @media (min-width: 993px) {
    $class: col-pc-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        width: ($n / 24) * 100%;
      }
    }
    $class: offset-pc-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        margin-left: ($n / 24) * 100%;
      }
    }
  }
  @media (min-width: 1201px) {
    $class: col-wide-pc-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        width: ($n / 24) * 100%;
      }
    }
    $class: offset-wide-pc-;
    @for $n from 1 through 24 {
      &.#{$class}#{$n} {
        margin-left: ($n / 24) * 100%;
      }
    }
  }
}
</style>
