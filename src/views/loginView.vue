<script setup>
import { useForm, useField } from 'vee-validate'
import { loginSchema as validationSchema} from '../validation/loginSchema'
import { useAuthStore } from '../stores/auth'

    const { handleSubmit } = useForm({validationSchema})
    const auth = useAuthStore()

    const  email  = useField('email')
    const  password  = useField('password')


    const submit = handleSubmit((values) => {
        auth.login(values)
    })

</script>

<template>

   

      <v-card
        flat
        width="600"
        class="mx-auto"
      >
        <v-card-title
            class="text-center text-h4 font-weight-bold"
            tag="h3"
        >
            Iniciar Sesión
        </v-card-title>
        <v-card-title
            class="text-center text-h5 mt-1"
        >
            Inicia Sesión con tu cuenta
        </v-card-title>

        <v-alert
                v-if="auth.hasError"
                class="my-5"
                :title="auth.errorMsg"
                type="error"
            ></v-alert>

        <v-form class="mt-5">
            <v-text-field 
                type="email"
                label="Email"
                bg-color="blue-grey-lighten-5"
                v-model="email.value.value"
                class="mt-5"
                :error-messages="email.errorMessage.value"
            />

            <v-text-field 
                type="password"
                label="Password"
                bg-color="blue-grey-lighten-5"
                v-model="password.value.value"  
                class="mt-2"
                :error-messages="password.errorMessage.value"  
            />

            <v-btn
                class="mt-5"
                block
                color="orange-lighten-1"
                @click="submit"
            >
                INICIAR SESIÓN
            </v-btn>

        </v-form>
      </v-card>
</template>

