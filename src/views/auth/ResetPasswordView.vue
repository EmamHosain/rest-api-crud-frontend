<script setup>
import { reactive, computed } from "vue";
import ValidationError from "@/components/auth/ValidationError.vue";
import useAuth from "@/composables/useAuth";
import { useAuthStore } from "@/stores/useAuthStore";
import SpinnerButton from "@/components/auth/SpinnerButton.vue";
import { useRoute } from "vue-router";

const { resetPassword } = useAuth();
const store = useAuthStore();
const errors = computed(() => store.errors)

const router = useRoute();

const data = reactive({
    loading: false,
    user: {
        email: router.query.email,
        token: router.params.token,
        password: '',
        password_confirmation: '',
    }
})

</script>


<template>
    <div class="flex min-h-full flex-col justify-center px-6 py-12 lg:px-8">
        <div class="sm:mx-auto sm:w-full sm:max-w-sm">
            <img class="mx-auto h-10 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600"
                alt="Your Company">
            <h2 class="mt-10 text-center text-2xl font-bold leading-9 tracking-tight text-gray-900">Reset your password
            </h2>
        </div>

        <div class="mt-10 sm:mx-auto sm:w-full sm:max-w-sm">
            <form class="space-y-6" @submit.prevent="resetPassword(data)">
                <div>
                    <label for="password" class="block text-sm font-medium leading-6 text-gray-900">New password</label>
                    <div class="mt-2">
                        <input v-model="data.user.password" id="password" type="password" placeholder="Enter new password"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset px-2 ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                    </div>
                    <validation-error v-if="errors" :errors="errors.password"></validation-error>
                </div>
                <div>
                    <label for="password_confirmation" class="block text-sm font-medium leading-6 text-gray-900">Confirm
                        password</label>
                    <div class="mt-2">
                        <input v-model="data.user.password_confirmation" id="password_confirmation" type="password"
                            placeholder="Enter confirm password"
                            class="block w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset px-2 ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6">
                    </div>
                </div>


                <div>
                    <spinner-button v-if="data.loading"></spinner-button>
                    <button v-else type="submit"
                        class="flex w-full justify-center rounded-md bg-indigo-600 px-3 py-1.5 text-sm font-semibold leading-6 text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Update
                        password</button>
                </div>
            </form>


        </div>
    </div>
</template>