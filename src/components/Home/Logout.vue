<template>
    
</template>

<script>
import AmplifyEventBus from "aws-amplify-vue";
import * as AmplifyUI from "@aws-amplify/ui";
import { Auth } from "aws-amplify";
export default {
  name: "SignOut",
  props: ["signOutConfig"],

  async beforeCreate() {
    Auth.signOut()
      .then(() => {
        this.$router.push("/signin");
        return AmplifyEventBus.$emit("authState", "signedOut");
      })
      .catch(e => this.setError(e));
  },

  methods: {
    setError: function(e) {}
  }
};
</script>