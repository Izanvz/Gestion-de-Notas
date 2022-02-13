<template>
  <q-page class="flex flex-center" padding>
    <div class="full-width" style="max-width: 300px">
      <h5 class="q-my-sm text-left text-primary">Register</h5>
      <q-card>
        <q-card-section>
          <q-input
            v-model="Nombre"
            square
            filled
            label="Nombre completo"
            placeholder="Manolo pica piedra"
            class="q-mb-sm"
            type="fullname"
            lazy-rules
            :rules="[requerido, valid_long]"
          >
          </q-input>
          <q-input
            v-model="Usuario"
            square
            filled
            label="User"
            placeholder="Example"
            class="q-mb-sm"
            type="username"
            lazy-rules
            :rules="[requerido, valid_long]"
          >
          </q-input>
          <q-input
            v-model="Dni"
            square
            filled
            label="Dni"
            placeholder="12345678Z"
            class="q-mb-sm"
            type="dni"
            lazy-rules
            :rules="[requerido, valid_long, valid_dni]"
          >
          </q-input>
          <q-input
            v-model="Contraseña"
            square
            filled
            label="Password"
            class="q-mb-sm"
            placeholder="* * * * * * *"
            :type="passwordFieldType"
            lazy-rules
            :rules="[requerido, valid_long]"
          >
          </q-input>
          <q-btn
            color="primary"
            class="full-width"
            label="Register"
            @click="register"
          />
          <div class="q-my-sm text-center">
            Tienes cuenta?
            <a href="http://localhost:8080/#/Login" class="text-primary"
              >Inicia session!</a
            >
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from 'vue'
import { useQuasar } from 'quasar'
export default defineComponent({
  name: 'Register',
  setup () {
    const $q = useQuasar()
    return {
      register () {
        $q.notify({
          message: 'Registrandose...',
          color: 'positive',
          timeout: 2000,
          progress: true
        })
      },
      requerido (val) {
        return (val && val.length > 0) || 'Debes rellenar el campo'
      },
      valid_long (val) {
        return (val && val.length > 5) || 'El nombre de usuario es demasiado corto'
      },
      valid_dni (val) {
        return (val && val.length === 9) || 'Dni no valido'
      }
    }
  },
  data () {
    return {
      Nombre: '',
      Usuario: '',
      Dni: '',
      Contraseña: '',
      passwordFieldType: 'password',
      visibility: false,
      alert: ref(false)
    }
  }
})
</script>
