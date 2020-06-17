<template>
  <div class="home">
    <Farewell msg="Hi, DockerLead!" />
  </div>
</template>

<script>
// @ is an alias to /src
import Farewell from "@/components/Farewell.vue";

export default {
  name: "Home",
  components: {
    Farewell
  }
};
</script>
