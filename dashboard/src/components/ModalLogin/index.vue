<template>
  <div class="flex justify-between">
    <h1 class="text-4xl font-black text-gray-800">Log in to your account</h1>
    <button @click="close" class="text-4xl text-gray-600">&times;</button>
  </div>
  <div class="mt-16">
    <form @submit.prevent="handleSubmit">
      <label class="block">
        <span class="text-lg font-medium text-gray-800">Email</span>
        <input
          v-model="state.email.value"
          type="email"
          placeholder="yourmail@email.com"
          :class="{ 'border-brand-danger': !!state.email.errorMessage }"
          class="block w-full px-4 py-3 mt-1 text-lg bg-gray-100 border-2 border-transparent rounded"
        />
        <span
          v-if="!!state.email.errorMessage"
          class="block font-medium text-brand-danger"
        >
          {{ state.email.errorMessage }}
        </span>
      </label>
      <label class="block">
        <span class="text-lg font-medium text-gray-800">Password</span>
        <input
          v-model="state.password.value"
          type="password"
          :class="{ 'border-brand-danger': !!state.password.errorMessage }"
          class="block w-full px-4 py-3 mt-1 text-lg bg-gray-100 border-2 border-transparent rounded"
        />
        <span
          v-if="!!state.password.errorMessage"
          class="block font-medium text-brand-danger"
        >
          {{ state.password.errorMessage }}
        </span>
      </label>
      <button
        :disabled="state.isLoading"
        type="submit"
        :class="{ 'opacity-50': state.isLoading }"
        class="px-8 py-3 mt-10 text-lg font-bold text-white rounded-full bg-brand-main transition-all duration-150"
      >
        Sign in
      </button>
    </form>
  </div>
</template>

<script>
import { reactive } from "vue";
import useModal from "../../hooks/useModal";

export default {
  setup() {
    const modal = useModal();

    const state = reactive({
      hasErrors: false,
      isLoading: false,
      email: {
        value: "",
        errorMessage: "",
      },
      password: {
        value: "",
        errorMessage: "",
      },
    });

    function handleSubmit() {}

    return {
      state,
      close: modal.close,
    };
  },
};
</script>
