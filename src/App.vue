<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-toolbar-title>Gestion des dépenses</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/CedricWagner/POC---CA-API-consumer"
        target="_blank"
        text
      >
        <span class="mr-2">Voir sur github</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <LoginForm v-if="!authenticated" @authenticated="setAuthenticated"></LoginForm>
      <OperationList v-if="authenticated"></OperationList>
    </v-main>
  </v-app>
</template>

<script>
import LoginForm from './components/LoginForm';
import OperationList from './components/OperationList';

export default {
  name: 'App',

  components: {
    LoginForm,
    OperationList,
  },

  data: () => ({
    authenticated: false,
  }),
  
  methods: {
    setAuthenticated(status) {
        this.authenticated = status;
    }
  }
};
</script>
