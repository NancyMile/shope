<script setup>
    import { reactive } from 'vue'
    import Alert from './Alert.vue'

    const alert = reactive({
        type: '',
        message: ''
    })

    defineEmits([
        'update:name',
        'update:owner',
        'update:email',
        'update:discharged',
        'update:symtoms'
    ])

    const props = defineProps({
        name:{
            type: String,
            required: true,
        },
        owner:{
            type: String,
            required: true
        },
        email:{
            type: String,
            required: true
        },
        discharged:{
            type: String,
            required: true
        },
        symtoms:{
            type: String,
            required: true,
        }
    })

    const validate = () => {
        if(Object.values(props).includes('')){
            //console.log('Some data is missing.')
            alert.message = 'Please fill everything.'
            alert.type ='error'
            return
        }
        console.log('validating ...')
    }

</script>

<template>
    <div class="md:w-1/2">
        <h2 class=" font-black text-3xl text-center">Patients Follow up</h2>
        <p class=" text-lg m-t-5 text-center mb-10">Add patients <span class=" text-indigo-600 font-bold">manage them</span> </p>

        <Alert
            v-if="(alert.message)"
            :alert="alert"
        />

        <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10"
            @submit.prevent="validate"
        >
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="pet">Pet Name</label>
                <input
                    id="pet"
                    type="text"
                    placeholder="Pet Name"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                    :value="name"
                    @input="$emit('update:name',$event.target.value)"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="owner">Owner Name</label>
                <input
                    id="owner"
                    type="text"
                    placeholder="Owner name"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                    :value="owner"
                    @input="$emit('update:owner', $event.target.value)"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="email">Email</label>
                <input
                    id="email"
                    type="email"
                    placeholder="email"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                    :value="email"
                    @input="$emit('update:email', $event.target.value)"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="email">Discharged</label>
                <input
                    id="discharged"
                    type="date"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                    :value="discharged"
                    @input="$emit('update:discharged',$event.target.value)"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="email">Symtoms</label>
                <textarea
                    id="sysmtoms"
                    placeholder="Symtoms"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md h-40"
                    :value="symtoms"
                    @input="$emit('update:symtoms',$event.target.value)"
                ></textarea>
            </div>
            <div class="mb-5">
                <input
                    type="submit"
                    value="Register"
                    class="w-full p-3 uppercase bg-indigo-600 text-white hover:bg-indigo-900 font-bold cursor-pointer transition-colors"
                />
            </div>
        </form>
    </div>
</template>