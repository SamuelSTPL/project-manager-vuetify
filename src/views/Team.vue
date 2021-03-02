<template>
  <div class="team">
    <v-subheader class="text--grey">Team</v-subheader>

    <v-container class="my-5">
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
          lg="6"
          v-for="person in team"
          :key="person.name"
        >
          <v-card flat class="text-center">
            hello
          </v-card>
        </v-col>
      </v-row>
    </v-container>

    <v-container class="my-5"> </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      team: [
        { name: "Anakin Sky-Vaper", role: "Web developer" },
        { name: "Obiwan 'Hello-There!' Kenobi", role: "Graphic Designer" },
        { name: "YO-da", role: "Web developer" },
        { name: "Ya Boy Vader", role: "Social media expert" },
        { name: "Qui-is-Gone", role: "Sales Guru" }
      ]
    };
  }
};
</script>
