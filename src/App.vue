<script setup>
import { ref, reactive, onMounted,watch } from "vue"
import { uid } from 'uid'
import Header from "./components/Header.vue"
import Form from "./components/Form.vue"
import Patient from "./components/Patient.vue"

const patients = ref([])

const patient = reactive({
  id: null,
  name: "",
  owner: "",
  email: "",
  discharged: "",
  symtoms: "",
})

onMounted(() => {
  const patientsStorage = localStorage.getItem('patients')
  if (patientsStorage) {
    patients.value = JSON.parse(patientsStorage)
  }
})

watch(patients, () => {
  saveLocalStorage()
}, {
  deep: true
})

const saveLocalStorage = () => {
  localStorage.setItem('patients', JSON.stringify(patients.value))
}

const savePatient = () => {
  if (patient.id) {
    //console.log('editing');
    const { id } = patient
    //find the position if this patient on patients array
    const index = patients.value.findIndex(patientState => patientState.id === id)
    patients.value[index] = { ... patient }
  } else {
    //console.log('Save patient')
    patients.value.push({ ...patient, id: uid() })
  }

  //clear
  Object.assign(patient, {
    name: "",
    owner: "",
    email: "",
    discharged: "",
    symtoms: "",
    id: null
  });
}

const updatePatient = (id) => {
  //onsole.log('updating patient ...')
  const editPatient = patients.value.filter(patient => patient.id === id)[0] //as is only one record
  Object.assign(patient, editPatient)
}

const deletePatient = (id) => {
  //onsole.log('delete patient ...')
  patients.value = patients.value.filter(patient => patient.id !== id)
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
        :id="patient.id"
      />

      <div class="md:w-1/2 md:h-screen overflow-y-scroll">
        <h3 class="font-black text-3xl text-center">Admin Patients</h3>
        <div v-if="patients.length > 0">
          <p class="text-lg m-t-5 text-center mb-10">
            Patiensts <span class="text-indigo-600 font-bold">Information</span>
          </p>
          <Patient
            v-for="patient in patients"
            :patient="patient"
            @update-patient="updatePatient"
            @delete-patient="deletePatient"
          />
        </div>
        <p v-else class="mt-20 text-2xl text-center">No patients.</p>
      </div>
    </div>
  </div>
</template>