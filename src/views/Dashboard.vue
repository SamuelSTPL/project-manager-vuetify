<template>
  <div class="dashboard">
    <v-subheader class="text--grey">Dashboard</v-subheader>

    <v-container class="my-5">
      <v-row class="mb-5 ml-1">
        <!-- To have a tooltip, first use the v-tooltip element  -->
        <!-- Then use the template element. Make sure to add the v-slot prop  -->
        <v-tooltip top>
          <template v-slot:activator="{ on }">
            <!-- The element inside must have the v-on="on" prop  -->
            <v-btn
              small
              flat
              depressed
              class="grey lighten-3 grey--text"
              @click="sortBy('title')"
              v-on="on"
            >
              <v-icon left small>mdi-folder</v-icon>
              <span class="caption text-lowercase">By project name</span>
            </v-btn>
          </template>
          <!-- The span under the template tag will define what text is shown in the tooltip  -->
          <span>Sorts projects by name</span>
        </v-tooltip>
        <v-tooltip top>
          <template v-slot:activator="{ on }">
            <v-btn
              small
              flat
              depressed
              class="grey lighten-3 grey--text"
              @click="sortBy('person')"
              v-on="on"
            >
              <v-icon left small>mdi-account</v-icon>
              <span class="caption text-lowercase">By person</span>
            </v-btn>
          </template>
          <span>Sorts projects by person</span>
        </v-tooltip>
      </v-row>

      <v-card flat tile v-for="project in projects" :key="project.title">
        <!-- V-Row used for applying the grid property  -->
        <!-- Use backtick to apply classes from the data along with vuetify or custom classes -->
        <v-row :class="`py-3 project ${project.status}`">
          <!-- xs breakpoint does not exist. Use cols instead-->
          <v-col cols="12" md="6">
            <div class="caption grey--text">Project Title</div>
            <div>{{ project.title }}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text">Person</div>
            <div>{{ project.person }}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="caption grey--text">Due by</div>
            <div>{{ project.due }}</div>
          </v-col>
          <v-col cols="6" sm="4" md="2">
            <div class="text-right pr-12">
              <v-chip
                small
                :class="
                  `v-chip-active white--text caption my-2 ${project.status}`
                "
              >
                {{ project.status }}
              </v-chip>
            </div>
          </v-col>
        </v-row>
        <v-col cols="12">
          <!-- Add a separation line  -->
          <v-divider></v-divider>
        </v-col>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Dashboard",
  data() {
    return {
      projects: [
        {
          title: "Design a new website",
          person: "Anakin Sky-Vaper",
          due: "1st Jan 5010",
          status: "ongoing",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },
        {
          title: "Code up the homepage",
          person: 'Obiwan "Hello-There!" Kenobi',
          due: "10th Jan 5010",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },
        {
          title: "Design video thumbnails",
          person: "YO-da",
          due: "20th Dec 2010",
          status: "complete",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        },
        {
          title: "Create a community forum",
          person: "Ya Boy Vader",
          due: "20th Oct 2010",
          status: "overdue",
          content:
            "Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!"
        }
      ]
    };
  },
  methods: {
    // Sort the project based on the prop (either person or title)
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1));
    }
  }
};
</script>

<style scoped>
.project.complete {
  border-left: 4px solid #3cd1c2;
  margin-left: 0;
}
.project.ongoing {
  border-left: 4px solid orange;
  margin-left: 0;
}
.project.overdue {
  border-left: 4px solid tomato;
  margin-left: 0;
}
.v-chip.complete {
  background: #3cd1c2 !important;
}
.v-chip.ongoing {
  background: #ffaa2c !important;
}
.v-chip.overdue {
  background: #f83e70 !important;
}
</style>
