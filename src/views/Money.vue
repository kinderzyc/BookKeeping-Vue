<template>
  <Layout class-prefix="layout">
    <NumberPad :value.sync="record.amount" @submit="saveRecord" />
    <Tabs :data-source="recordTypeList" :value.sync="record.type" />
    <div class="createdAt">
      <Notes field-name="日期" type="date" placeholder="请输入日期" :value.sync="record.createdAt" />
    </div>
    <div class="notes">
      <Notes field-name="备注" placeholder="请输入备注名" :value.sync="record.notes" />
    </div>
    <Tags @update:value="record.tags = $event" />
  </Layout>
</template>

<script lang="ts">
import Vue from "vue";
import NumberPad from "../components/Money/NumberPad.vue";
import Notes from "../components/Money/Notes.vue";
import Tags from "../components/Money/Tags.vue";
import Tabs from "../components/Tabs.vue";
import { Component } from "vue-property-decorator";
import store from "../store/index";
import recordTypeList from "../constants/recordTypeList";


@Component({
  components: { NumberPad, Tabs, Notes, Tags }
})
export default class Money extends Vue {
  get recordList() {
    return this.$store.state.recordList;
  }
  recordTypeList = recordTypeList;

  record: RecordItem = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0,
    createdAt: new Date().toISOString()
  };

  created() {
    this.$store.commit("fetchRecords");
  }

  onUpdateNotes(value: string) {
    this.record.notes = value;
  }
  saveRecord() {
    if (!this.record.tags || this.record.tags.length === 0) {
      return window.alert("请至少选择一个标签！");
    }
    this.$store.commit("createRecord", this.record);
    if (this.$store.state.createRecordError === null) {
      window.alert("已保存");
      this.record.notes = "";
    }
  }
}
</script>
<style lang="scss" >
.layout-content {
  display: flex;
  flex-direction: column-reverse;
}
</style>

