<template>
    <v-container>
      <v-row>
        <v-col :sm="1" :md="3" :lg="4"></v-col>
        <v-col :sm="10" :md="6" :lg="4">
            <v-card width="100%">
                <v-img
                    height='10rem'
                    src="/images/login.png"
                >
                </v-img>
                <v-card style="padding: 1rem">
                    <v-text-field
                        outlined
                        label="Full Name *"
                        append-icon="mdi-account"
                        v-model="fullname"
                    ></v-text-field>
                    <v-text-field
                        outlined
                        label="Email *"
                        append-icon="mdi-mail"
                        v-model="email"
                        type='email'
                    ></v-text-field>
                    <v-text-field
                        outlined
                        label="Username *"
                        append-icon="mdi-account"
                        v-model="username"
                        :rules="rules.username"
                    ></v-text-field>
                    <v-text-field
                        outlined
                        label="Password *"
                        append-icon="mdi-lock"
                        type="password"
                        v-model="password"
                        :rules="rules.password"
                    ></v-text-field>
                    <v-text-field
                        outlined
                        label="Confirm Password *"
                        append-icon="mdi-lock"
                        type="password"
                        v-model="confirmPassword"
                        :rules="rules.password"
                    ></v-text-field>
                    <v-alert
                        v-if="error"
                        dense
                        outlined
                        type="error"
                    >
                        <strong>username</strong> or <strong>password</strong> is wrong
                    </v-alert>
                    <v-card-actions>
                        <v-btn
                            color="primary"
                            height="3rem"
                            width="40%"
                            @click="register()"
                        > Confirm </v-btn>
                    </v-card-actions>
                </v-card>
            </v-card>
        </v-col>
        <v-col :sm="1" :md="3" :lg="4"></v-col>
      </v-row>
    </v-container>
</template>

<script>
export default {
    data() {
        return {
            username: '',
            password: '',
            fullname: '',
            email: '',
            confirmPassword: '',
            rules: {
                username: [val => !val && 'username is required'],
                password: [val => !val && 'password is required']
            },
            error: false
        }
    },
    methods: {
        register() {
            console.log(this.username, this.password)
            this.error = !this.error
            this.$router.push("/login")
        }
    }
}
</script>