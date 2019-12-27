<template>
  <v-app app dark>
    <v-navigation-drawer app v-model="drawer">
      <v-list subheader>
        <v-subheader>Пользователи в комнате</v-subheader>

        <v-list-item v-for="u in users" :key="u.id" >
          
          <v-list-item-content>
            <v-list-item-title v-text="u.name"></v-list-item-title>
          </v-list-item-content>

          <v-list-item-icon>
            <v-icon :color="u.id === 2 ? 'deep-purple accent-4' : 'grey'"
              >mdi-message</v-icon
            >
          </v-list-item-icon>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-btn icon @click="exit">
        <v-icon>mdi-arrow-left-thick</v-icon>
      </v-btn>
      <v-toolbar-title>Комната {{ user.room }}</v-toolbar-title>
    </v-app-bar>
    <v-content app>
      <div>
        <nuxt />
      </div>
    </v-content>
  </v-app>
</template>

<script>
import { mapState, mapMutations } from "vuex";

export default {
  data: () => ({
    drawer: false,
    users: [
      {id: 1, name: 'user1'},
      {id: 2, name: 'user2'}
    ]
  }),
  computed: {
    ...mapState(["user"])
  },
  methods: {
    ...mapMutations(['clearData']),
    exit() {
      this.$router.push('/?message=leftChat');
      this.clearData();
    }
  }
};
</script>
