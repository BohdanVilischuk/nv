<template>
  <section class="section">
    <Search/>
    <Filters />
    <Users />
  </section>
</template>

<script>
import Users from "~/components/Users.vue";
import Search from "~/components/Search";
import Filters from "~/components/Filters";

export default {
  name: 'HomePage',

  components: {
    Filters,
    Search,
    Users
  }
}
</script>
