<template>
  <q-page class="flex flex-center" padding>
    <div class="full-width" style="max-width: 300px">
      <h5 class="q-my-sm text-center text-primary">Informacion</h5>
      <q-card>
        <q-card-section>
          <div>
            <br>
            Autor : {{autor}}
            <br>
            Contacto : {{correo}}
            <br>
            <br>
            Fecha inicio : {{fecha_inicio}}
            <br>
          </div>
        </q-card-section>
      </q-card>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'About',
  data () {
    return {
      autor: 'Izan Villarejo',
      correo: 'izanvillarejo2002@gmail.com',
      fecha_inicio: '10/02/2022'
    }
  }
})
</script>
