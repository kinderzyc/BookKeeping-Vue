<template>
  <Layout class-prefix="layout">
    <NumberPad :value.sync="record.amount" @submit="saveRecord" />
    <Types :value.sync="record.type" />
    <Notes field-name="备注" placeholder="请输入备注名" @update:value="onUpdateNotes" />
    <Tags :data-source.sync="tags" @update:value="onUpdateTags" />
  </Layout>
</template>

<script lang="ts">
import Vue from "vue";
import NumberPad from "../components/Money/NumberPad.vue";
import Types from "../components/Money/Types.vue";
import Notes from "../components/Money/Notes.vue";
import Tags from "../components/Money/Tags.vue";
import { Component } from "vue-property-decorator";
import store from "../store/index2";
// import recordListModel from "../models/recordListModel";
// import tagListModel from "../models/tagListModel";

// const recordList = recordListModel.fetch()

// type RecordItem = {
//   tags: string[];
//   notes: string;
//   type: string;
//   amount: number; //数据类型
//   createAt?: Date; // 类 /构造函数
// };

@Component({
  components: { NumberPad, Types, Notes, Tags }
})
export default class Money extends Vue {
  tags = store.tagList;
  recordList = store.recordList;
  record: RecordItem = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0
  };
  onUpdateTags(value: string[]) {
    this.record.tags = value;
  }

  onUpdateNotes(value: string) {
    this.record.notes = value;
  }
  saveRecord() {
    store.createRecord(this.record);
  }
}
</script>
<style lang="scss">
.layout-content {
  display: flex;
  flex-direction: column-reverse;
}
</style>

