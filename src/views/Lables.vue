<template>
  <Layout>
    <ol class="tags">
      <li v-for="tag in tags" :key="tag">
        <span>{{tag}}</span>
        <Icon name="rights" />
      </li>
    </ol>
    <div class="createTags-wrapper">
      <button class="createTags" @click="createTag">新建标签</button>
    </div>
  </Layout>
</template>

<script lang="ts">
import Vue from "vue";
import tagListModel from "../models/tagListModel";
import { Component } from "vue-property-decorator";

tagListModel.fetch();

@Component
export default class Lables extends Vue {
  tags = tagListModel.data;

  createTag() {
    const name = window.prompt("请输入标签名");
    if (name) {
      const message = tagListModel.create(name);
      if (message === "duplicated") {
        window.alert("标签重复了");
      } else if (message === "success") {
        window.alert("添加成功");
      }
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
  > li {
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
