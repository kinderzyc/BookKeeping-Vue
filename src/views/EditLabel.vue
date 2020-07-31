<template>
  <Layout>
    <div class="navBar">
      <Icon class="leftIcon" name="back" />
      <span class="title">编辑标签</span>
      <span class="rightIcon"></span>
    </div>
    <Notes field-name="标签名" placeholder="请输入标签名" />
    <div class="button-wrapper">
      <Button>删除标签</Button>
    </div>
  </Layout>
</template>

<script lang="ts">
import Vue from "vue";
import { Component } from "vue-property-decorator";
import VueRouter, { Route } from "vue-router";
import tagListModel from "../models/tagListModel";
import Notes from "../components/Money/Notes.vue";
import Button from "../components/Button.vue";

@Component({
  components: { Notes, Button }
})
export default class EditLabel extends Vue {
  created() {
    const id = this.$route.params.id;
    tagListModel.fetch();
    const tags = tagListModel.data;
    const tag = tags.filter(t => t.id === id)[0];
    if (tag) {
      console.log(tag);
    } else {
      this.$router.replace("/404");
    }
  }
}
</script>

<style lang="scss" scoped>
.navBar {
  text-align: center;
  font-size: 20px;
  font-weight: bolder;
  padding: 12px 16px;
  background: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
  > .leftIcon {
    width: 32px;
    height: 32px;
  }
  > .rightIcon {
    width: 32px;
    height: 32px;
  }
}
.button-wrapper {
  text-align: center;
  padding: 16px;
  margin-top: 20px;
}
</style>