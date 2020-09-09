<template>
  <div class="card link-card">
    <header class="card-header">
      <p class="card-header-title">
        Component
        <a class="remove button is-danger">
          <span class="icon">
            <i class="fas fa-trash-alt"></i>
          </span>
        </a>
      </p>
    </header>
    <div class="card-content">
      <div class="content">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus nec
        iaculis mauris.
        <a href="#">@bulmaio</a>. <a href="#">#css</a>
        <a href="#">#responsive</a>
        <br />
        <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
      </div>
    </div>
    <footer class="card-footer">
      <a href="#" class="card-footer-item">Access</a>
      <!-- <a href="#" class="card-footer-item">Remove</a> -->
    </footer>
  </div>
</template>
<script>
export default {
  name: "LinkCard",
};
</script>
