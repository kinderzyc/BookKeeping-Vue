<template>
  <div class="tags">
    <ul class="current">
      <li>衣</li>
      <li>食</li>
      <li>住</li>
      <li>行</li>
    </ul>
    <div class="new">
      <button>新增标签</button>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: "Tags"
};
</script>

<style lang="scss" scoped>
.tags {
  font-size: 20px;
  padding: 16px;
  display: flex;
  flex-grow: 1;
  flex-direction: column;
  > .current {
    display: flex;
    flex-wrap: wrap;
    > li {
      background: #d9d9d9;
      $h: 28px;
      height: $h;
      line-height: $h;
      border-radius: $h/2;
      padding: 0 26px;
      margin-right: 12px;
      margin-top: 4px;
      font-weight: bold;
    }
  }
  > .new {
    padding-top: 18px;
    button {
      background: transparent;
      border: none;
      color: #999;
      border-bottom: 1px solid;
      padding: 0 4px;
    }
  }
}
</style>