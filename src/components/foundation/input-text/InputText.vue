<template>
  <div class="field input-text">
    <label class="label is-large has-text-light">{{ label }}</label>
    <div class="control">
      <input
        class="input is-large"
        type="text"
        v-model="content"
        @input="change"
        :placeholder="placeholder"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "InputText",
  props: {
    value: {
      type: String,
    },
    label: {
      type: String,
      default: "Text",
    },
    placeholder: {
      type: String,
      default: "Text",
    },
  },
  data() {
    return {
      content: this.value,
    };
  },
  watch: {
    value() {
      this.content = this.value;
    },
  },
  methods: {
    change() {
      this.$emit("update:value", this.content);
    },
  },
};
</script>
