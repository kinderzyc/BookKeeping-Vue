<template>
  <Layout class-prefix="layout">
    <NumberPad :value.sync="record.amount" @submit="saveRecord" />
    <Types :value.sync="record.type" />
    <Notes field-name="备注" placeholder="请输入备注名" @update:value="onUpdateNotes" />
    <Tags />
  </Layout>
</template>

<script lang="ts">
import Vue from "vue";
import NumberPad from "../components/Money/NumberPad.vue";
import Types from "../components/Money/Types.vue";
import Notes from "../components/Money/Notes.vue";
import Tags from "../components/Money/Tags.vue";
import { Component } from "vue-property-decorator";
import store from "../store/index";

@Component({
  components: { NumberPad, Types, Notes, Tags },
  computed: {
    recordList() {
      return this.$store.state.recordList;
    }
  }
})
export default class Money extends Vue {
  record: RecordItem = {
    tags: [],
    notes: "",
    type: "-",
    amount: 0
  };

  created() {
    this.$store.commit("fetchRecords");
  }

  onUpdateNotes(value: string) {
    this.record.notes = value;
  }
  saveRecord() {
    this.$store.commit("createRecord", this.record);
  }
}
</script>
<style lang="scss">
.layout-content {
  display: flex;
  flex-direction: column-reverse;
}
</style>

