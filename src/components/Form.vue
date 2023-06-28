<script setup>

</script>

<template>
    <div class="md:w-1/2">
        <h2 class=" font-black text-3xl text-center">Patients Follow up</h2>
        <p class=" text-lg m-t-5 text-center mb-10">Add patients <span class=" text-indigo-600 font-bold">manage them</span> </p>

        <form class="bg-white shadow-md rounded-lg py-10 px-5 mb-10">
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="pet">Pet Name</label>
                <input
                    id="pet"
                    type="text"
                    placeholder="Pet Name"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="owner">Owner Name</label>
                <input
                    id="owner"
                    type="text"
                    placeholder="Owner name"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="email">Email</label>
                <input
                    id="email"
                    type="email"
                    placeholder="email"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="email">Discharged</label>
                <input
                    id="discharged"
                    type="date"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md"
                />
            </div>
            <div class="mb-5">
                <label class="block text-gray-600 uppercase font-bold" for="email">Symtoms</label>
                <textarea
                    id="sysmtoms"
                    placeholder="Symtoms"
                    class="border-2 w-full p-2 mt-2 placeholder:gray-400 rounded-md h-40"
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