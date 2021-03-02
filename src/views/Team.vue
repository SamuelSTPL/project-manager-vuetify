<template>
  <div class="team">
    <v-container class="my-5">
      <v-row>
        <v-col
          cols="12"
          sm="6"
          md="4"
          lg="3"
          v-for="person in team"
          :key="person.name"
        >
          <v-card flat class="text-center ma-3">
            <v-row>
              <v-col class="mt-5 text-center">
                <!-- Use the v-avatar tag to add avatar. Nest a img tag inside -->
                <v-avatar size="80" class="grey lighten-2">
                  <img :src="person.avatar" />
                </v-avatar>
              </v-col>
            </v-row>
            <v-card-text>
              <div class="text-subtitle-1">{{ person.name }}</div>
              <div class="grey--text">{{ person.role }}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn depressed class="grey--text mb-1">
                <v-icon small left>mdi-message</v-icon>
                <span>Message</span>
              </v-btn>
            </v-card-actions>
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
        {
          name: "Anakin Sky-Vaper",
          role: "Web developer",
          avatar: "/avatar.png"
        },
        {
          name: "Obiwan 'Hello-There!' Kenobi",
          role: "Graphic Designer",
          avatar: "/avatar.png"
        },
        { name: "YO-da", role: "Web developer", avatar: "/avatar.png" },
        {
          name: "Ya Boy Vader",
          role: "Social media expert",
          avatar: "/avatar.png"
        },
        { name: "Qui-is-Gone", role: "Sales Guru", avatar: "/avatar.png" }
      ]
    };
  }
};
</script>
