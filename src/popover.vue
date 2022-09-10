<template>
  <div class="g-popover" ref="popover">
    <div
      class="content-wrapper"
      v-if="isVisable"
      :class="`position-${position}`"
      ref="contentWrapper"
    >
    弹出内容
      <slot name="content"></slot>
    </div>
    <span ref="triggleWrapper" class="triggle">
      <slot></slot>
    </span>
  </div>
</template>

<script>
export default {
  components: {},
  props: {
    position: {
      type: String,
      default: "top",
      validator(value) {
        return ["top", "bottom", "left", "right"].indexOf(value) >= 0;
      },
    },
    triggle: {
      type: String,
      default: "click",
      validator(value) {
        return ["click", "hover"].indexOf(value) >= 0;
      },
    },
  },
  data() {
    return {
      isVisable: false,
    };
  },
  watch: {},
  computed: {},
  methods: {
    positionContent() {
      document.body.appendChild(this.$refs.contentWrapper);
      const { left, top, height, width } =
        this.$refs.triggleWrapper.getBoundingClientRect();
      const { contentWrapper } = this.$refs;
      const { height: contentHeight } = contentWrapper.getBoundingClientRect();
      const positions = {
        top: {
          left: `${left + window.scrollX}px`,
          top: `${top + window.scrollY}px`,
        },
        bottom: {
          left: `${left + window.scrollX}px`,
          top: `${top + height + window.scrollY}px`,
        },
        left: {
          left: `${left + window.scrollX}px`,
          top: `${top - (contentHeight - height) / 2 + window.scrollY}px`,
        },
        right: {
          left: `${left + width + window.scrollX}px`,
          top: `${top - (contentHeight - height) / 2 + window.scrollY}px`,
        },
      };
      //设置弹框相对于按钮的位置
      contentWrapper.style.left = positions[this.position].left;
      contentWrapper.style.top = positions[this.position].top;
    },
    onClickDocument(e) {
      if (
        this.$refs.popover &&
        (this.$refs.popover === e.target ||
          this.$refs.popover.contains(e.target))
      ) {
        return;
      }
      if (
        this.$refs.contentWrapper &&
        (this.$refs.contentWrapper === e.target ||
          this.$refs.contentWrapper.contains(e.target))
      ) {
        return;
      }
      this.close();
    },
    close() {
      this.isVisable = false;
      document.removeEventListener("click", this.onClickDocument);
    },
    onShow() {
      this.isVisable = true;
      this.$nextTick(() => {
        this.positionContent();
        document.addEventListener("click", this.onClickDocument);
      });
    },
    onClick(event) {
      if (this.$refs.triggleWrapper.contains(event.target)) {
        if (this.isVisable) {
          this.close();
        } else {
          this.onShow();
        }
      }
    },
    removePopoverListeners() {
      if (this.trigger === "click") {
        this.$refs.popover.removeEventListener("click", this.onClick);
      } else {
        this.$refs.popover.removeEventListener("mouseenter", this.open);
        this.$refs.popover.removeEventListener("mouseleave", this.close);
      }
    },
    putBackContent() {
      const { contentWrapper, popover } = this.$refs;
      if (!contentWrapper) {
        return;
      }
      popover.appendChild(contentWrapper);
    },
  },
  mounted() {
    if (this.triggle === "click") {
      this.$refs.popover &&
        this.$refs.popover.addEventListener("click", this.onClick);
    } else {
      this.$refs.popover &&
        this.$refs.popover.addEventListener("mouseenter", this.onShow);
      this.$refs.popover &&
        this.$refs.popover.addEventListener("mouseleave", this.close);
    }
  },
  beforeDestroy() {
    this.putBackContent();
    this.removePopoverListeners();
  },
};
</script>
<style scoped lang='scss'>
.g-popover {
  display: inline-block;
  vertical-align: top;
  position: relative;
}
.content-wrapper {
  position: absolute;
  border: 1px solid #333;
  filter: drop-shadow(0 1px 1px rgba(0, 0, 0, 0.5));
  border-radius: 4px;
  background: white;
  padding: 0.5em 1em;
  max-width: 20em;
  word-break: break-all;
  &::before,
  &::after {
    display: block;
    content: "";
    border: 10px solid transparent;
    width: 0;
    height: 0;
    position: absolute;
  }
  &.position-top {
    transform: translateY(-100%);
    margin-top: -10px;
    &::before,
    &::after {
      left: 10px;
    }
    &::before {
      border-top-color: black;
      top: 100%;
    }
    &::after {
      border-top-color: white;
      top: calc(100% - 1px);
    }
  }
  &.position-bottom {
    margin-top: 10px;
    &::before,
    &::after {
      left: 10px;
    }
    &::before {
      border-bottom-color: black;
      bottom: 100%;
    }
    &::after {
      border-bottom-color: white;
      bottom: calc(100% - 1px);
    }
  }
  &.position-left {
    transform: translateX(-100%);
    margin-left: -10px;
    &::before,
    &::after {
      top: 50%;
      transform: translateY(-50%);
    }
    &::before {
      border-left-color: black;
      left: 100%;
    }
    &::after {
      border-left-color: white;
      left: calc(100% - 1px);
    }
  }
  &.position-right {
    margin-left: 10px;
    &::before,
    &::after {
      top: 50%;
      transform: translateY(-50%);
    }
    &::before {
      border-right-color: black;
      right: 100%;
    }
    &::after {
      border-right-color: white;
      right: calc(100% - 1px);
    }
  }
}
.triggle {
  display: inline-block;
}

</style>
