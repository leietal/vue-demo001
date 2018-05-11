<template>
<div class="hello">
  <div class="hello-header right">
    <div class="header-title">
      <span>系统提示</span>
    </div>
    <div class="header-tools">
      <i class="icon icon-enlarge"></i>
      <i class="icon icon-narrow"></i>
      <i class="icon icon-close"></i>
    </div>
  </div>
  <div class="hello-body">
    <span>{{data.content}}</span>
  </div>
</div>
</template>

<script>
export default {
  name: 'Chart',
  props: {
    data: {
      type: Object
    }
  },
  components: {},
  data() {
    return {}
  },
  mounted() {
    console.log(`chart${this.data.i} mounted`)
    this.$emit('updateLayout', this.data);
  }
}
</script>

<style scoped>
.hello {
  margin: 10px;
  background-color: #43CD80;
  color: #282828;
  padding: 10px;
  border-radius: 3px;
}

.hello-header {
  display: flex;
  flex-wrap: nowrap;
  justify-content: space-between;
  align-items: center;
  color: #FFFFFF;
  font-size: 14px;
  cursor: move;
}

.header-title,
.header-tools {
  flex-grow: 0;
  flex-shrink: 0;
}

.hello-body {
  margin-top: 10px;
  padding: 10px;
  border-radius: 3px;
  background-color: #3CB371;
  color: #FFFFFF;
}

.center {
  text-align: center;
}

.right {
  text-align: right;
}

.icon::after {
  color: #FFFFFF;
  display: inline-block;
  height: 16px;
  width: 16px;
  text-align: center;
  border-radius: 8px;
  line-height: 16px;
  background-color: #3CB371;
  cursor: pointer;
  font-style: normal;
}

.icon-enlarge::after {
  content: '+';
}

.icon-narrow::after {
  content: '-';
}

.icon-close::after {
  content: '×';
}
</style>
