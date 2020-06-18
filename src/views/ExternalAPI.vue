<template>
  <div>
    <b-button variant="primary" @click="callApi">Call API</b-button>
    <b-toast
      id="api-toast"
      variant="success"
      toast-class="b-toaster-top-right"
      title="API Call Results"
      auto-hide-delay="3000"
    >
      {{ apiMessage }}
    </b-toast>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "external-api",
  data() {
    return {
      apiMessage: ""
    };
  },
  methods: {
    async callApi() {
      // Get the access token from the auth wrapper
      const token = await this.$auth.getTokenSilently();

      // Use Axios to make a call to the API
      const { data } = await axios.get("/api/external", {
        headers: {
          Authorization: `Bearer ${token}` // send the access token through the 'Authorization' header
        }
      });
      this.apiMessage = data.msg;
      this.$bvToast.show("api-toast");
    }
  }
};
</script>
