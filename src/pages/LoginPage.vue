<template>
    <q-page padding>
        <q-card style="width: 500px; margin: 0 auto" class="rounded">
            <q-card-section>
                <div class="text-h6 text-center q-pb-sm">
                    <q-icon
                        name="familiar_face_and_zone"
                        size="64px"
                        color="teal"
                    />
                    <q-icon name="school" size="64px" color="teal" />
                </div>
                <q-separator />
                <div
                    class="text-center"
                    style="
                        font-size: 1.5rem;
                        margin-top: 1.5rem;
                        color: teal;
                        font-weight: bold;
                    "
                >
                    Welcome to eLearning
                </div>
                <div
                    class="text-center q-mb-lg"
                    style="font-size: 0.8rem; color: teal"
                >
                    Sign in to continue
                </div>
                <q-separator></q-separator>
            </q-card-section>
            <q-card-section>
                <q-form ref="loginForm">
                    <q-input
                        filled
                        v-model="credentials.username"
                        label="Enter you username"
                        type="text"
                        lazy-rules
                        :rules="[
                            (val) =>
                                (val && val.length > 0) ||
                                'Username is a required field!',
                        ]"
                    >
                        <template v-slot:append>
                            <q-icon name="person" />
                        </template>
                    </q-input>
                    <q-input
                        filled
                        v-model="credentials.password"
                        label="Enter your password"
                        type="password"
                        class="q-mt-sm"
                        :rules="[
                            (val) =>
                                (val && val.length > 0) ||
                                'Password is a required field!',
                        ]"
                    >
                        <template v-slot:append>
                            <q-icon name="key" /> </template
                    ></q-input>
                </q-form>
            </q-card-section>
            <q-card-actions class="q-mr-sm q-pb-lg" align="center">
                <q-btn
                    padding=".5rem 6rem"
                    color="secondary"
                    @click="evnt_login()"
                    >Log in</q-btn
                >
            </q-card-actions>
        </q-card>
    </q-page>
</template>

<script>
import { defineComponent, ref } from "vue";
export default defineComponent({
    name: "LoginPage",
    setup() {
        const credentials = ref({ username: "", password: "" });
        const loginForm = ref(null);

        function evnt_login() {
            loginForm.value.validate().then((is_valid) => {
                console.log(is_valid);
            });
        }

        return { credentials, loginForm, evnt_login };
    },
});
</script>
