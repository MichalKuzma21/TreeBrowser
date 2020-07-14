<template>
  <div>
    <div
      @click="expanded = !expanded"
      :style="{ 'margin-left': `${depth * 20}px` }"
      class="node"
    >
      <span v-if="hasChildren" class="type">{{
        expanded ? "&#9660;" : "&#9658;"
      }}</span>
      <span v-if="!hasChildren" class="type"> &#9900; </span>
      {{ node.name }}
    </div>
    <template v-if="expanded">
      <TreeBrowser
        v-for="child in node.nodes"
        :key="child.name"
        :node="child"
        :depth="depth + 1"
      />
    </template>
  </div>
</template>

<script>
export default {
  name: "TreeBrowser",
  props: {
    node: Object,
    depth: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      expanded: false,
    };
  },
  computed: {
    hasChildren() {
      return this.node.nodes.length > 0;
    },
  },
};
</script>

<style scoped>
.node {
  text-align: left;
  font-size: 18px;
}
</style>
