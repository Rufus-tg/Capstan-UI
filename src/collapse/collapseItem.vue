<template>
  <div class="g-collapse-item" >
    <div class="title" @click="toggle">
      <div>{{ title }}</div>
      <icon :name='iconName' class="collapse-icon"></icon>
      </div>
    <div class="content" v-if="open">
    <slot></slot>
    </div>
  </div>
</template>

<script>
import Icon from '../icon.vue';
export default {
  components: {Icon},
  props: {
    title: {
      type: String,
      required: true,
    },
    name:{
      type: String
    }
  },
  data() {
    return {
      open: false,
      single: false
    };
  },
  computed: {
    iconName() {
      return this.open ? 'down' : 'right';
    }
  },
  inject: ['eventBus'],
  methods: {
    toggle() {
      if(this.open) {
        this.close();
      } else {
        this.show();
        this.eventBus && this.eventBus.$emit('update:selected', this.name);
      }
    },
    close() {
      this.open = false;
    },
    show() {
      this.open = true;
    }
  },
  mounted() {
    // this.eventBus.$on('update:selected', (event)=> {
    //     if(event !== this.name) {
    //       if(this.single){
    //         this.close();
    //       }
    //     } else {
    //       this.show();
    //     }
    // });
  },
};
</script>
<style scoped lang='scss'>
$border-radius: 4px;
.g-collapse-item {
  >.title {
    border: 1px solid #ddd;
    margin-left: -1px;
    margin-top: -1px;
    margin-right: -1px;
    min-height: 40px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 8px;
  }
  &:first-child{
    >.title {
      border-top-left-radius: $border-radius;
      border-top-right-radius: $border-radius;
    }
  }
  &:last-child{
    >.title:last-child {
      border-bottom-left-radius: $border-radius;
      border-bottom-right-radius: $border-radius;
    }
  }
  >.content {
    padding: 8px;
  }
}
  .collapse-icon {
    fill: #aaa;
  }
</style>
