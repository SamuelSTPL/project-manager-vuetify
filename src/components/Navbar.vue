<template>
  <nav>
    <v-app-bar app flat>
      <!-- The @Clicl Toggle the drawer menu -->
      <v-app-bar-nav-icon
        class="grey--text"
        @click="drawer = !drawer"
      ></v-app-bar-nav-icon>
      <v-app-bar-title class="text-uppercase grey--text">
        <span class="font-weight-light">Todo</span>
        <span>Sam</span>
      </v-app-bar-title>

      <v-spacer>
        <!-- Split to fill up the space from both component  -->
      </v-spacer>

      <v-btn text color="grey">
        <span>Sign Out</span>
        <v-icon right>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- Left menu Navigation  -->
    <v-navigation-drawer v-model="drawer" app class="primary">
      <v-row>
        <v-col class="text-center mt-10">
          <v-avatar size="100">
            <img src="/avatar.png" />
          </v-avatar>
          <p class="white--text text-subtitle-1 mt-1">Sam STPL</p>
        </v-col>
      </v-row>
      <v-list class="d-flex flex-column ml-5">
        <v-list-item
          v-for="link in links"
          :key="link.text"
          class="mt-10"
          link
          :to="link.route"
        >
          <v-list-item-action>
            <v-icon left class="white--text">{{ link.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">
              {{ link.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
  data() {
    return {
      // If true, menu will open
      drawer: false,
      links: [
        { icon: "mdi-view-dashboard", text: "Dashboard", route: "/" },
        { icon: "mdi-folder", text: "My Projects", route: "/projects" },
        { icon: "mdi-account", text: "Team", route: "/team" }
      ]
    };
  }
};
</script>
