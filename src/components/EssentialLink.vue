<template>
  <!--  4. Modifica els víncles. Tots t’han de dirigir a
  altres parts de l’aplicació sobre la mateixa pestanya. -->

  <!-- usando target="_blank" en vez de _self, se abre en una nueva pestaña -->
  <!-- <q-item clickable tag="a" target="_blank" :href="link"> -->
  <q-item clickable tag="a" target="_self" :href="link">
    <q-item-section v-if="icon" avatar>
      <q-icon class="q-ml-sm" :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>
        {{ caption }}
      </q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
import { defineComponent } from 'vue'
export default defineComponent({
  name: 'EssentialLink',
  props: {
    title: {
      type: String,
      required: true
    },
    caption: {
      type: String,
      default: ''
    },
    link: {
      type: String,
      default: '#'
    },
    icon: {
      type: String,
      default: ''
    }
  }
})
</script>
