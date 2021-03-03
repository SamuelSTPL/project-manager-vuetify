<template>
  <!-- Use v-dialog element to create the Popup  -->
  <v-dialog max-width="600px" v-model="dialog">
    <template v-slot:activator="{ on }">
      <v-btn text class="success" v-on="on">Add new project</v-btn>
    </template>

    <v-card>
      <v-card-title>
        Add a New Project
      </v-card-title>

      <!-- Form element  -->
      <v-card-text>
        <v-form class="px-3" ref="form">
          <v-text-field
            label="Title"
            v-model="title"
            prepend-icon="mdi-folder"
            :rules="inputRules"
          ></v-text-field>
          <v-textarea
            label="Information"
            v-model="content"
            prepend-icon="mdi-pencil"
            :rules="inputRules"
          ></v-textarea>

          <!-- Create the calendar input  -->
          <v-menu max-width="290">
            <template v-slot:activator="{ on }">
              <v-text-field
                :value="formattedDate"
                label="Due date"
                prepend-icon="mdi-calendar-range"
                v-on="on"
                :rules="inputRules"
              ></v-text-field>
            </template>
            <v-date-picker v-model="due"></v-date-picker>
          </v-menu>

          <v-btn
            depressed
            class="success mx-0 mt-3"
            @click="submit"
            :loading="loading"
            >Add Project</v-btn
          >
        </v-form>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
import format from "date-fns/format";
import parseISO from "date-fns/parseISO";
import db from "../fb";

export default {
  data() {
    return {
      title: "",
      content: "",
      due: null,
      inputRules: [(v) => v.length >= 3 || "Minimum length is 3 characters"],
      loading: false,
      dialog: false
    };
  },
  methods: {
    // Use the $ref to target the correct form element
    // The .validate is a methods that check all fields
    submit() {
      if (this.$refs.form.validate()) {
        this.loading = true;

        const project = {
          title: this.title,
          content: this.content,
          due: format(parseISO(this.due), "do MMM yyyy"),
          person: "Anakin Sky-Vaper",
          status: "ongoing"
        };
        // Add the new object to firebase
        db.collection("projects")
          .add(project)
          .then(() => {
            this.loading = false;
            this.dialog = false;
            this.$emit("projectAdded");
          })
          .catch((err) => console.log(err));
      }
    }
  },
  computed: {
    formattedDate() {
      return this.due ? format(parseISO(this.due), "do MMM yyyy") : "";
    }
  }
};
</script>
