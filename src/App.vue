<template>
  <v-app>
    <v-main>
      <div
        style="background-color: #4da6ff; color: white; font-size: 24px"
        class="pa-2 text-center d-flex justify-center"
      >
        <v-dialog max-width="400">
          <template v-slot:activator="{ props: activatorProps }">
            <v-btn
              v-bind="activatorProps"
              rounded="lg"
              elevation="0"
              class="mr-6"
              style="background-color: #4da6ff"
            >
              <v-icon style="font-size: 24px">mdi-account</v-icon>
            </v-btn>
          </template>

          <template v-slot:default="{ isActive }">
            <v-card rounded="xl">
              <v-card-title class="mx-auto">Log in</v-card-title>
              <v-container class="pt-0">
                <v-text-field
                  prepend-inner-icon="mdi-account"
                  class="mb-2"
                  hide-details
                  label="Name"
                  variant="outlined"
                  density="compact"
                ></v-text-field>
                <v-text-field
                  prepend-inner-icon="mdi-key"
                  class="mt-2"
                  hide-details
                  label="Password"
                  variant="outlined"
                  density="compact"
                ></v-text-field>
              </v-container>
              <div class="d-flex justify-center mb-3">
                <v-btn
                  color="green"
                  variant="tonal"
                  text="Submit"
                  @click="isActive.value = false"
                ></v-btn>
              </div>
            </v-card>
          </template>
        </v-dialog>

        <p>Eye tracker app</p>
        <v-btn
          rounded="lg"
          elevation="0"
          class="ml-6"
          style="background-color: #4da6ff"
        >
          <v-icon>mdi-bell </v-icon>
        </v-btn>
      </div>
      <v-row class="py-8">
        <v-col cols="9">
          <v-container
            style="border: 2px solid gray; border-radius: 24px; height: 80vh"
          >
          </v-container>
        </v-col>
        <v-col cols="3" class="d-flex justify-center align-center flex-column">
          <v-container>
            <div class="d-flex align-center">
              <span class="mr-4">X coordinate</span>
              <v-text-field
                hide-details
                variant="outlined"
                density="compact"
                label="value"
                v-model="Coordinate.xCoordinate"
              ></v-text-field>
            </div>
            <div class="d-flex align-center mt-4">
              <span class="mr-4">Y coordinate</span>
              <v-text-field
                hide-details
                variant="outlined"
                density="compact"
                label="value"
                v-model="Coordinate.yCoordinate"
              ></v-text-field>
            </div>
          </v-container>
          <div class="d-flex justify-space-around mb-3">
            <v-btn
              @click="addCoordinate()"
              color="green"
              width="150"
              opacity="2"
              class="mx-4"
              ><v-icon>mdi-content-save</v-icon></v-btn
            >
            <v-btn
              @click="checkNotes = !checkNotes"
              color="blue"
              width="150"
              opacity="2"
              class="mx-4"
              ><v-icon>mdi-pencil</v-icon></v-btn
            >
          </div>
          <div class="d-flex my-2" v-for="item in totalCoordinates" :key="item">
            <div class="px-2">
              xCoordinate: <span> {{ item?.x }} </span>
            </div>
            <div class="px-2">
              yCoordinate: <span> {{ item?.y }} </span>
            </div>
            <hr />
          </div>
        </v-col>
      </v-row>

      <v-navigation-drawer
        width="500"
        location="right"
        temporary
        v-model="checkNotes"
      >
        <v-sheet>
          <h2 class="pa-2 text-center" style="color: #4da6ff; font-weight: 400">
            <v-icon class="mr-2">mdi-eye</v-icon> Coordinate notes
          </h2>
          <hr class="mb-6" />
          <div v-for="item in totalCoordinates" :key="item">
            <v-hover>
              <template v-slot:default="{ isHovering, props }">
                <v-card
                  v-bind="props"
                  style="cursor: pointer; border: 2px solid #4da6ff"
                  rounded="lg"
                  class="my-2 ml-6 pa-4 pr-0 d-flex justify-space-between align-center"
                  variant="outlined"
                  :color="isHovering ?  '#4da6ff' : undefined"
                >
                  <div
                    color="#4da6ff"
                  >
                    x: {{ item?.x }} y: {{ item?.y }} {{ item?.date }}
                  </div>
                  <v-btn rounded="md" height="36px" width="36px" icon="mdi-pen" ></v-btn>
                </v-card>
              </template>
            </v-hover>
          </div>
        </v-sheet>
      </v-navigation-drawer>

      <div
        style="background-color: #4da6ff; color: white; font-size: 24px"
        class="pa-4 text-center"
      >
        Team 3 Human computer interaction 2024
      </div>
    </v-main>
  </v-app>
</template>

<script>
import moment from "moment";

export default {
  name: "App",
  data() {
    return {
      Coordinate: {
        xCoordinate: 0,
        yCoordinate: 0,
      },
      totalCoordinates: [],
      checkNotes: false,
    };
  },
  methods: {
    addCoordinate() {
      this.totalCoordinates.push({
        x: this.Coordinate.xCoordinate,
        y: this.Coordinate.yCoordinate,
        date: moment(new Date()).format("YYYY-MM-DD-ны өдрийн HH:mm:SS"),
      });
    },
    noteCoordinates() {},
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Commissioner:wght@100..900&display=swap");
* {
  font-family: "Commissioner", sans-serif;
}

.selectedClass {
  background-color: #4da6ff;
}

.notSelectedClass {
  background-color: white;
}
</style>
