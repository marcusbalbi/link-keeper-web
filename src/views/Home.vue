<template>
  <div class="home hero">
    <h1 class="hero-title main-title title is-1 mb-1">Link Keeper</h1>
    <div class="home-content hero-body">
      <div class="container is-fluid">
        <form class="link-form columns">
          <InputText
            v-model:value.sync="form.title"
            label="Title"
            placeholder="Ex: My first attempt"
            class="column"
          />
          <InputText
            v-model:value.sync="form.link"
            label="Link"
            class="column"
            placeholder="http://youtube.com/text"
          />
          <InputText
            v-model:value.sync="form.domain"
            label="Domain"
            class="column"
            placeholder="Youtube"
          />
          <div class="actions buttons column is-narrow">
            <button class="button is-primary is-large">
              <span class="icon is-small">
                <i class="fas fa-lg fa-plus"></i>
              </span>
            </button>
            <button class="button is-danger is-large">
              <span class="icon is-small">
                <i class="fas fa-lg fa-broom"></i>
              </span>
            </button>
          </div>
        </form>
      </div>
      <div class="container is-fluid">
        <div class="links-list columns">
          <div v-for="link in links" :key="link" class="card link-card">
            <header class="card-header">
              <p class="card-header-title">
                Component
              </p>
            </header>
            <div class="card-content">
              <div class="content">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                Phasellus nec iaculis mauris.
                <a href="#">@bulmaio</a>. <a href="#">#css</a>
                <a href="#">#responsive</a>
                <br />
                <time datetime="2016-1-1">11:09 PM - 1 Jan 2016</time>
              </div>
            </div>
            <footer class="card-footer">
              <a href="#" class="card-footer-item">Access</a>
              <a href="#" class="card-footer-item">Remove</a>
            </footer>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import InputText from "../components/foundation/input-text/InputText";
export default {
  name: "Home",
  components: { InputText },
  data() {
    return {
      form: {
        title: "BALBI",
        link: "",
        domain: "",
      },
      links: [{ title: "", link: "", domain: "" }],
    };
  },
};
</script>
<style lang="scss">
.main-title {
  text-align: center;
  font-weight: 200;
  cursor: pointer;
}
</style>
