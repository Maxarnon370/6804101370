<template>
  <q-page class="q-pa-md">
    <q-form class="q-gutter-md" style="max-width: 400px" @submit="onSubmit" @reset="onReset">
    
      <q-input filled v-model="name" label="Your name *" hint="Name and surname" />
      <q-input filled type="number" v-model="age" label="Your age *" />
      <q-toggle v-model="accept" class="no-wrap" label="I accept the license and terms (我接受许可和条款语言)" />

      <div>
        <q-btn label="SUBMIT" type="submit" color="primary" />
        <q-btn label="RESET" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue'
import { useQuasar } from 'quasar'

const $q = useQuasar()
const name = ref('')
const age = ref(null)
const accept = ref(false)

function onSubmit () {
  if (accept.value !== true) {
    $q.notify({
      type: 'negative',
      message: 'You need to accept the license and terms first'
    })
  } else {
    $q.notify({
      type: 'positive',
      message: 'Submitted successfully'
    })
  }
}

function onReset () {
  name.value = ''
  age.value = null
  accept.value = false
}
</script>