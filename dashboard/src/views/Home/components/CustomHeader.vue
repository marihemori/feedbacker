<template>
  <header class="header">
    <div class="flex flex-col w-4/5 max-w-6xl">
      <div class="flex items-center justify-between py-10">
        <div class="w-28 lg:w-36">
          <img
            class="w-full"
            src="../../../assets/images/logo_white.png"
            alt="Logo"
          />
        </div>

        <div class="flex">
          <button
            @click="() => emit('create-account')"
            class="px-6 py-2 font-bold rounded-full text-white"
          >
            Create an account
          </button>
          <button
            @click="() => emit('login')"
            class="px-6 py-2 font-bold bg-white rounded-full text-brand-main"
          >
            Login
          </button>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  setup(_, { emit }) {
    return { emit };
  },
};
</script>

<style lang="postcss" scoped>
.header {
  @apply bg-brand-main w-full flex justify-center;
  height: fit-content;
}
</style>
