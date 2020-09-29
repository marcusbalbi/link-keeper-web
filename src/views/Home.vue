<template>
  <div class="home hero">
    <h1 class="hero-title main-title title is-1 mb-1">Link Keeper</h1>
    <div class="home-content hero-body">
      <div class="container is-fluid">
        <form @submit.prevent="add" class="link-form columns">
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
        <ul class="links-list columns">
          <li v-for="link in links" :key="link">{{ link.title }}</li>
        </ul>
        <footer>
          Pagination
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import InputText from "../components/foundation/input-text/InputText";
// import LinkCard from "../components/foundation/link-card/LinkCard";
import request from "../request/request";

export default {
  name: "Home",
  components: { InputText },
  data() {
    return {
      form: {
        title: "",
        link: "",
        domain: "",
      },
      links: [
        { id: "", title: "", link: "", domain: "" },
        { title: "", link: "", domain: "" },
        { title: "", link: "", domain: "" },
        { title: "", link: "", domain: "" },
        { title: "", link: "", domain: "" },
        { title: "", link: "", domain: "" },
        { title: "", link: "", domain: "" },
      ],
    };
  },
  methods: {
    add() {
      request
        .post("/bookmarks/", this.form)
        .then(() => {
          this.listAll();
          this.cleanForm();
        })
        .catch((err) => {
          console.log(err);
        });
    },
    remove(link) {
      request
        .delete("/bookmarks/".concat(link._id))
        .then(() => {
          this.listAll();
        })
        .catch((err) => {
          console.log(err);
        });
    },
    cleanForm() {
      this.form.title = "";
      this.form.link = "";
      this.form.domain = "";
    },
    listAll() {
      return request
        .get("/bookmarks")
        .then((result) => {
          this.links = Array.from(result.data.data);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
  mounted() {
    this.listAll();
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
