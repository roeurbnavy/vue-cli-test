<template>
  <div class="hello">
    <div class="header">
      <slot name="header"></slot>
    </div>
    <h1>From Parent msg :: {{ msg }}</h1>
    <br />
    <ul>
      <li v-for="(it, key) in items" :key="key">
        {{ it }}
      </li>
    </ul>
    <br />
    <button class="button" @click="toParent">To Parent</button>

    <div class="footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";

const props = defineProps({
  msg: String,
  items: Array,
});

const emits = defineEmits(["toParent"]);

const toParent = () => {
  props.items.forEach((it) => {
    it.total = it.qty * it.price;
  });
  emits("toParent", { details: props.items, msg: "From Child" });
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.header {
  height: 50px;
  background: #04aa6d;
}

.footer {
  height: 50px;
  background: red;
}
</style>
