<template>
  <Layout>
    <div class="tags">
      <router-link class="tag" v-for="tag in tags" :key="tag.id" :to="`/labels/edit/${tag.id}`">
        <span>{{tag.name}}</span>
        <Icon name="rights" />
      </router-link>
    </div>
    <div class="createTags-wrapper">
      <Button class="createTags" @click="createTag">新建标签</Button>
    </div>
  </Layout>
</template>

<script lang="ts">
import Vue from "vue";
import { Component } from "vue-property-decorator";
import Button from "../components/Button.vue";
// import store from "../store/index2";

@Component({
  components: {Button}
})
export default class Lables extends Vue {
  // tags = store.tagList;
  tags = [] //todo

  createTag() {
    const name = window.prompt("请输入标签名");
    if (name) {
      //todo
      // store.createTag(name);
    }
  }
}
</script>

<style lang="scss" scoped>
.tags {
  width: 90%;
  margin: 0 auto;
  background: white;
  font-size: 18px;
  margin-top: 20px;
  font-weight: bold;
  > .tag {
    /* box-shadow: 1px 1px 6px #aaaaaa; */
    border: 1px solid #aaaaaa;
    min-height: 60px;
    display: flex;
    align-items: center;
    border-radius: 8px;
    justify-content: space-between;
    padding-left: 18px;
    margin-bottom: 20px;
    svg {
      color: #aaaaaa;
      width: 1.5em;
      height: 1.5em;
      margin-right: 8px;
    }
  }
}
.createTags {
  background: #767676;
  box-shadow: 1px 1px 9px #767676;
  color: white;
  border-radius: 8px;
  border: none;
  height: 40px;
  padding: 0 16px;
  margin-top: 20px;
  &-wrapper {
    text-align: center;
  }
}
</style>
