<template>
  <div class="master">
    <SiteTop :title="title" />
    <div class="container">
      <div class="body">
        <h4>{{ message?.title }}</h4>
        <span class="editor" v-html="message?.message"></span>
      </div>

      <div class="link">
        <NuxtLink :to="localePath('/list')">{{
          $store.state.translations["list_title"]
        }}</NuxtLink>
      </div>
    </div>
    <Loader v-if="loading" />
  </div>
</template>

<script>
import messagesApi from "@/api/messages";
import Loader from "~/components/loader.vue";

export default {
  data() {
    return {
      title: "Xabarni ko'rish",
      message: {},
      loading: false,
    };
  },
  async mounted() {
    if (localStorage.getItem("authToken")) {
      this.loading = true;
      const hotel = await messagesApi.getMessageById(this.$axios, {
        id: this.$route.params.id,
        params: {
          headers: {
            Authorization: `Bearer ${localStorage.getItem("authToken")}`,
          },
        },
      });
      this.message = hotel?.data;
      this.loading = false;
    } else {
      this.$router.push(this.localePath("/auth"));
    }
  },
  components: { Loader },
};
</script>

<style scoped>
.container {
  padding: 56px 0 112px 0;
}
.container h4 {
  color: var(--Blue-dark, #002856);
  font-family: var(--semi);
  font-size: var(--24);
  font-style: normal;
  font-weight: 600;
  line-height: 140%; /* 33.6px */
  margin-bottom: 32px;
  display: flex;
  max-width: 952px;
  margin: 0 auto 24px auto;
}
.body {
  max-width: 1200px;
  margin: 0 auto;
}
.body .editor {
  display: flex;
  flex-direction: column;
  max-width: 952px;
  margin: 0 auto 24px auto;
}
.body :deep(p) {
  color: var(--grey-80, #353437);
  font-size: var(--16);
  font-style: normal;
  font-weight: 400;
  line-height: 150%;
  margin-bottom: 24px;
}
.body :deep(img) {
  width: 100%;
  height: 620px;
  object-fit: cover;
  border-radius: 32px;
  display: flex;
}
.link {
  display: flex;
  justify-content: center;
}
.link a {
  display: flex;
  margin-top: 12px;
  border-radius: 16px;
  border: 1px solid var(--Agro-Blue, #00b55d);
  padding: 18px 50px;
  color: var(--Agro-Blue, #00b55d);
  font-family: var(--semi);
  font-size: var(--14);
  font-style: normal;
  font-weight: 600;
  line-height: 140%; /* 19.6px */
  transition: 0.4s;
}
.link a:hover {
  background: #00b55d;
  color: white;
}
@media screen and (max-width: 1024px) {
  .container {
    overflow: hidden;
    padding: 40px 16px;
  }
  .body img {
    height: 198px;
    border-radius: 20px;
  }
}
</style>
