<template>
  <div id="sidebar">
    <el-button
      @click="toggleSidebar"
      type="text"
      id="close"
      icon="el-icon-close"
    ></el-button>
    <el-menu
      background-color="#222831"
      text-color="#fff"
      active-text-color="#30A2E2"
      class="el-menu-vertical-demo"
      default-active="1"
    >
      <div class="my-5 d-flex flex-column justify-center">
        <div class="avatar bg-light mx-auto"></div>
        <h6 class="text-center text-light mt-3">Amanam Israel</h6>
        <p class="badge bg-light-primary text-primary text-center m-0 mx-auto">
          Admin
        </p>
      </div>
      <div class="menu">
        <el-menu-item class="is-active" index="1" @click="toOverview">
          <ion-icon name="grid-outline" class="mr-3"></ion-icon>
          <span tag="span" slot="title">Overview</span>
        </el-menu-item>
        <el-menu-item index="2" @click="toTickets">
          <ion-icon name="ticket-outline" class="mr-3"></ion-icon>
          <span slot="title">Tickets</span>
        </el-menu-item>
        <el-menu-item index="3" @click="toVendors">
          <ion-icon name="people-outline" class="mr-3"></ion-icon>
          <span slot="title">Vendors</span>
        </el-menu-item>
        <el-menu-item index="4" @click="toBlog">
          <ion-icon name="book-outline" class="mr-3"></ion-icon>
          <span slot="title">Blog</span>
        </el-menu-item>
        <el-menu-item index="5" @click="toRentals">
          <ion-icon name="key-outline" class="mr-3"></ion-icon>
          <span slot="title">Rentals</span>
        </el-menu-item>
      </div>
      <div class="logout-container p-3">
        <div class="d-flex justify-content-center w-100">
          <el-button
            type="danger"
            class="p-2 logout-btn text-light"
            @click="logout"
            >Log out</el-button
          >
        </div>
      </div>
    </el-menu>
  </div>
</template>

<script>
export default {
  name: "sidebar",
  data() {
    return {};
  },
  methods: {
    toRentals() {
      this.$router.push("/dashboard/rentals").catch(() => {});
      this.checkWindow();
    },
    toTickets() {
      this.$router.push("/dashboard/tickets").catch(() => {});
      this.checkWindow();
    },
    toVendors() {
      this.$router.push("/dashboard/vendors").catch(() => {});
      this.checkWindow();
    },
    toBlog() {
      this.$router.push("/dashboard/blog").catch(() => {});
      this.checkWindow();
    },
    toOverview() {
      this.$router.push("/dashboard").catch(() => {});
      this.checkWindow();
    },
    checkWindow() {
      if (window.matchMedia("(max-width: 576px)").matches) {
        this.toggleSidebar();
      }
    },
    toggleSidebar() {
      document.getElementById("sidebar").classList.toggle("active");
      document.getElementById("content").classList.toggle("active");
    },
    logout() {
      localStorage.clear();
      this.$router.push({ path: "/" });
    },
  },
};
</script>

<style lang="scss">
#sidebar {
  min-width: 300px;
  max-width: 300px;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  z-index: 998;
  height: 100vh;

  .el-menu {
    height: 100%;
  }
}
.active {
  margin-left: -300px;
}
.avatar {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}
.badge {
  padding: 1em;
  width: min-content;
}
#close {
  position: absolute;
  right: 0;
  top: 17px;
  z-index: 99;
  padding: 1em;
  display: none;
}
@media screen and (max-width: 576px) {
  #sidebar {
    margin-left: -300px;
  }
  #sidebar.active {
    margin-left: 0;
  }
  #close {
    display: block;
  }
}
div.logout-container {
  height: calc(100vh - 520px);
  display: flex;
  align-items: flex-end;
}
</style>