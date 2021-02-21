<template>
    <v-container>
        <v-form
            v-model="valid"
        >
            <v-text-field
                v-model="email"
                :counter="50"
                :rules="[rules.email,rules.required]"
                label="Email"
                required
            ></v-text-field>
            <v-text-field
                v-model="password"
                :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                :rules="[rules.required]"
                :type="show ? 'text' : 'password'"
                name="input-password"
                label="Mot de passe"
                required
                @click:append="show = !show"
          ></v-text-field>

            <v-btn
                :disabled="!valid"
                color="success"
                class="mr-4"
                @click="login"
                >
                Se connecter
            </v-btn>
            <v-alert
                v-if="error"
                type="error"
            >
                {{ error }}
            </v-alert>

        </v-form>
    </v-container>
</template>

<script>
    export default {
        name: 'LoginForm',

        data() {
            return {
                show: false,
                valid: false,
                error: false,
                password: '',
                email: '',
                rules: {
                    required: value => !!value || 'Required.',
                    email: value => /.+@.+/.test(value) || 'E-mail must be valid',
                },
                mockAccount: {
                    email: "test@test.fr",
                    password: "123"
                }
            }
        },

        methods: {
            login() {
                if(this.email == this.mockAccount.email && this.password == this.password) {
                    this.$emit("authenticated", true);
                } else {
                    this.error = "The email and / or password is incorrect";
                }
            }
        },
    }
</script>