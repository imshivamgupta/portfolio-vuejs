<template>
  <div id="app">
    <Container>
      <Header :darkMode="darkMode" />
    </Container>
    <Container>
      <transition name="slither">
        <router-view />
      </transition>
    </Container>
    <SocialMedia />
  </div>
</template>

<script>
import { mapState } from "vuex";
import Header from "@/components/Header";
import Container from "@/components/Utilities/Container";
import SocialMedia from "@/components/Utilities/SocialMedia";
export default {
  name: "App",
  components: {
    Header,
    Container,
    SocialMedia,
  },
  data() {
    return {
      bgColor: "#00ff00",
      height: "60",
    };
  },
  computed: {
    ...mapState(["darkMode"]),
    headerVars() {
      return {
        "--bg-color": this.bgColor,
        "--height": this.height + "px",
      };
    },
  },
  created() {
    console.log("created");
    this.unsubscribe = this.$store.subscribe((mutation, { user }) => {
      if (mutation.type === "darkMode") {
        const htmlDOM = window.document.querySelector("html");
        htmlDOM.setAttribute("theme", user.darkMode ? "dark" : "lite");
      }
    });
  },
  beforeDestroy() {
    this.unsubscribe();
  },
};
</script>

<style lang="scss">
.slither-enter-active,
.slither-leave-active {
  transition: transform 0.4s linear;
}

.slither-enter,
.slither-leave-to {
  transform: translateY(100%);
}

.slither-enter-to,
.slither-leave {
  transform: translateY(0);
}
</style>

