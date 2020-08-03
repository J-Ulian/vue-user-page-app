<template>
  <section>
    <h1>{{ pageTitle }}</h1>

    <img src="../assets/portrait.jpg" alt="portrait" />

    <p>
      <strong>Username:</strong>
      admin
    </p>
    <p>
      <strong>Email:</strong>
      hudatov@gmail.com
    </p>
  </section>
</template>

<script>
export default {
  async fetch({ store }) {
    if (store.getters["users/users"].length === 0) {
      await store.dispatch("users/fetch");
    }
  },
  data: () => ({
    pageTitle: "My Profile"
  }),
  computed: {
    users() {
      return this.$store.getters["users/users"];
    }
  },
  methods: {
    openUser(user) {
      this.$router.push("/users/" + user.id);
    }
  },
  middleware: ["auth"]
};
</script>
