<template>
  <div class="card link-card">
    <header class="card-header">
      <p class="card-header-title">
        {{ small_title }}
        <a @click="$emit('remove')" class="remove button is-danger">
          <span class="icon">
            <i class="fas fa-trash-alt"></i>
          </span>
        </a>
      </p>
    </header>
    <div class="card-content">
      <div class="content">
        <span>{{ data.title }}</span>
        -
        <span class="domain">{{ data.domain }}</span>
      </div>
    </div>
    <footer class="card-footer">
      <a :href="data.link" target="_blank" class="card-footer-item">Access</a>
    </footer>
  </div>
</template>
<script>
export default {
  name: "LinkCard",
  props: {
    data: {
      type: Object,
      default() {
        return {
          title: "title",
        };
      },
    },
  },
  computed: {
    small_title() {
      if (this.data.title.length > 25) {
        return this.data.title.substr(0, 25).concat("...");
      }
      return this.data.title;
    },
  },
};
</script>
