<template>
  <button
    @click="
      () => {
        removeTodo(i);
      }
    "
  >
    Remove
  </button>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";
import { Task } from "../Models/task";
import { Prop } from "vue-property-decorator";

@Options({
  components: {},
})
export default class RemoveTodo extends Vue {
  @Prop() Task!: Task[];

  removeTodo(i: number) {
    this.$emit("removeTodo", i);
  }
}
</script>

<style lang="scss"></style>
