<template>
  <v-app>
    <v-main>
      <div
        style="background-color: blue; color: white; font-size: 24px"
        class="pa-2 text-center d-flex justify-center"
      >
        <v-btn class="mr-6" style="background-color: blue;"> <v-icon style="font-size: 24px;">mdi-bell</v-icon> </v-btn>
        <p>Eye tracker app</p>
        <v-btn class="ml-6" style="background-color: blue;"> <v-icon style="font-size: 24px;">mdi-account </v-icon> </v-btn>
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
              <v-text-field label="value"></v-text-field>
            </div>
            <div class="d-flex align-center">
              <span class="mr-4">Y coordinate</span>
              <v-text-field label="value"></v-text-field>
            </div>
          </v-container>
          <div class="d-flex justify-space-around">
            <v-btn color="green" width="150" opacity="2" class="mx-4"
              ><v-icon>mdi-content-save</v-icon></v-btn
            >
            <v-btn color="blue" width="150" opacity="2" class="mx-4"
              ><v-icon>mdi-pencil</v-icon></v-btn
            >
          </div>
        </v-col>
      </v-row>

      <div
        style="background-color: blue; color: white; font-size: 24px"
        class="pa-4 text-center"
      >
        Team 3 Human computer interaction 2024
      </div>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: "App",
};
</script>
