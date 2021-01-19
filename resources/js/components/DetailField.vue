<template>
  <panel-item :field="fieldLabel" />
</template>

<script>
let vm;

export default {
  data() {
    return {
      tags: "",
      fieldLabel: {},
      tagsWrapperClass: "nti-tags-wrapper",
      tagClass: "nti-tag",
    };
  },
  props: ["resource", "resourceName", "resourceId", "field"],
  mounted() {
    vm = this;
    this.fieldLabel = this.field;

    if (this.field.value) {
      let items = this.field.value;
      items.forEach(function (item, index) {
        let label = item;
        vm.tags += '<span class="' + vm.tagClass + '">' + label + "</span>";
      });

      this.fieldLabel.value =
        '<div class="' + this.tagsWrapperClass + '">' + this.tags + "</div>";
      this.fieldLabel.asHtml = true;
    }
  },
};
</script>
