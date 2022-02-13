<template>
  <q-page class="flex flex-center" padding>
    <div class="full-width" style="max-width: 300px">
      <h5 class="q-my-sm text-left text-primary">Login</h5>
      <q-card>
        <q-card-section>
          <q-input
            v-model="Usuario"
            square
            filled
            label="User"
            placeholder="Example"
            class="q-mb-sm"
            type="username"
            lazy-rules
            :rules="[required, short]"
          >
          </q-input>
          <q-input
            v-model="Contraseña"
            square
            filled
            label="Password"
            class="q-mb-sm"
            placeholder="Demasiado debil."
            :type="passwordFieldType"
            lazy-rules
            :rules="[required, short]"
          >
          </q-input>
          <q-btn
            color="primary"
            class="full-width"
            label="Login"
            @click="login"
          />
          <div class="q-my-sm text-center">
            Aún no tienes cuenta?
            <a href="http://localhost:8080/#/register" class="text-primary"
              >Regístrate!</a
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
  name: 'Login',
  setup () {
    const $q = useQuasar()
    return {
      login () {
        $q.notify({
          message: 'Iniciando session...',
          color: 'positive',
          timeout: 2000,
          progress: true
        })
      },
      required (val) {
        return (val && val.length > 0) || 'Debes rellenar el campo'
      },
      short (val) {
        return (val && val.length > 5) || 'El nombre de usuario es demasiado corto'
      }
    }
  },
  data () {
    return {
      Usuario: '',
      Contraseña: '',
      passwordFieldType: 'password',
      visibility: false,
      alert: ref(false)
    }
  }
})
</script>
