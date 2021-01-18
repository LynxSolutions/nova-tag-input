<template>
  <div v-html="fieldLabel"></div>
</template>

<script>
let vm;

export default {
  data() {
    return {
      tags: "",
      fieldLabel: "",
      tagsWrapperClass: "nti-tags-wrapper",
      tagClass: "nti-tag",
    };
  },
  props: ["resourceName", "field"],
  mounted() {
    vm = this;
    this.newField = this.field;
    this.fieldLabel = '<div class="' + this.tagsWrapperClass + '">';
    if (this.field.value) {
      let items = JSON.parse(this.field.value);

      if (items.length) {
        let others = items.length > 1 ? " and others" : "";

        vm.tags +=
          '<span class="' + vm.tagClass + '">' + items[0] + others + "</span>";
      }

      this.fieldLabel += vm.tags;
    }
    this.fieldLabel += "</div>";
  },
};
</script>
