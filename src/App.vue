<template>
<div class="app">
  <v-app id="inspire">
    <v-navigation-drawer
   v-model="drawer"
   app
   >
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Todo-App
          </v-list-item-title>
          <v-list-item-subtitle>
            Daily To-do List
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

 <v-app-bar
      app
      dark
      src="mountain.jpg"
      prominent
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-app-bar-title>Todo</v-app-bar-title>

      <v-spacer></v-spacer>
 
      <v-navigation
      v-model="value"
      :input-value="active"
      color="indigo"
      >

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon
      :outline="active"
     @click="active = !active"
      >
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>

        </v-navigation>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
    </div>
</template>

<script>
  export default {
    data: () => ({
      drawer: null,
      items: [
        { title: 'Todo', icon: 'mdi-format-list-checks', to:'/' },
          { title: 'About', icon: 'mdi-help-box', to:'/about' },
        ],
      }),
  }
</script>

<style>
 .v-main__wrap {
    flex: 1 1 auto;
    max-width: 100%;
    position: relative;
    background-color: lightgray;
}

.v-sheet.v-list:not(.v-sheet--outlined) {
  background-color: lightgray;
}

.v-list-item.v-list-item--link.theme--light {
    background-color: white;
}
</style>