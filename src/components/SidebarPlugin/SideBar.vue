<template>
  <nav
    class="navbar navbar-vertical fixed-left navbar-expand-md navbar-light bg-white"
    id="sidenav-main"
  >
    <div class="container-fluid">
      <!--Toggler-->
      <navbar-toggle-button @click.native="showSidebar"> </navbar-toggle-button>
      <!-- <router-link class="navbar-brand" to="/"> </router-link> -->

      <slot name="mobile-right">
        <ul class="nav align-items-center d-md-none">
          <a slot="title-container" class="nav-link" href="#" role="button">
            <div class="media align-items-center">
              <span class="avatar avatar-sm rounded-circle">
                <img
                  alt="Image placeholder"
                  src="img/portfolio/my-profile.png"
                />
              </span>
            </div>
          </a>
        </ul>
      </slot>
      <slot></slot>
      <div
        v-show="$sidebar.showSidebar"
        class="navbar-collapse collapse show"
        id="sidenav-collapse-main"
      >
        <div class="navbar-collapse-header d-md-none">
          <div class="row">
            <div class="font-weight-bold col-6 collapse-brand">
              Front-End Developer I.Sak
            </div>
            <div class="col-6 collapse-close">
              <navbar-toggle-button
                @click.native="closeSidebar"
              ></navbar-toggle-button>
            </div>
          </div>
        </div>

        <ul class="navbar-nav">
          <slot name="links"> </slot>
        </ul>
        <!--Divider-->
        <!-- <hr class="my-3"> -->
      </div>
    </div>
  </nav>
</template>
<script>
import NavbarToggleButton from "@/components/NavbarToggleButton";

export default {
  name: "sidebar",
  components: {
    NavbarToggleButton
  },
  props: {
    logo: {
      type: String,
      default: "img/brand/green.png",
      description: "Sidebar app logo"
    },
    autoClose: {
      type: Boolean,
      default: true,
      description:
        "Whether sidebar should autoclose on mobile when clicking an item"
    }
  },
  provide() {
    return {
      autoClose: this.autoClose
    };
  },
  methods: {
    closeSidebar() {
      this.$sidebar.displaySidebar(false);
    },
    showSidebar() {
      this.$sidebar.displaySidebar(true);
    }
  },
  beforeDestroy() {
    if (this.$sidebar.showSidebar) {
      this.$sidebar.showSidebar = false;
    }
  }
};
</script>
