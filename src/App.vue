<script setup>
import { ref, reactive } from "vue"
import Header from "./components/Header.vue"
import Form from "./components/Form.vue"

const patients = ref([])

const patient = reactive({
  name: "",
  owner: "",
  email: "",
  discharged: "",
  symtoms: "",
})

const savePatient = () => {
  console.log('Save patient')
}
</script>

<template>
  <div class="container mx-auto mt-20">
    <Header />
    <div class="mt-12 md:flex">
      <Form
        v-model:name="patient.name"
        v-model:owner="patient.owner"
        v-model:email="patient.email"
        v-model:discharged="patient.discharged"
        v-model:symtoms="patient.symtoms"
        @save-patient="savePatient"
      />

      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Admin Patients</h3>
        <div v-if="patients.length > 0"></div>
        <p v-else class="mt-20 text-2xl text-center">No patients.</p>
      </div>
    </div>
  </div>
</template>