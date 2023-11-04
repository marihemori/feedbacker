<template>
  <CustomHeader @create-account="handleAccountCreate" @login="handleLogin" />
  <main class="py-44 blue-balloons">
    <div class="flex flex-col w-4/5 max-w-6xl">
      <h1 class="text-5xl font-black text-white">
        Get a real feedback.
        <br />
        And make your customers <br class="hidden lg:inline-block" />
        happier!
      </h1>
      <p class="text-lg font-medium text-white mt-6">
        Receive ideas, complaints and feedback with a simple widget on the page.
      </p>
      <div>
        <button
          class="px-6 py-2 font-bold bg-white rounded-full text-brand-main mt-10"
        >
          Create a new account
        </button>
      </div>
    </div>
  </main>
  <Contact />
  <footer class="flex justify-center py-10 bg-brand-gray">
    <p class="font-medium text-center text-gray-800">feedbacker © 2023</p>
  </footer>
</template>

<script>
import { onMounted } from "vue";
import { useRouter } from "vue-router";
import CustomHeader from "./components/CustomHeader.vue";
import Contact from "./components/Contact.vue";
import useModal from "../../hooks/useModal";

export default {
  components: { CustomHeader, Contact },

  setup() {
    const router = useRouter();
    const modal = useModal();

    onMounted(() => {
      const token = window.localStorage.getItem("token");
      if (token) {
        router.push({ name: "Feedbacks" });
      }
    });

    function handleLogin() {
      modal.open({
        component: "ModalLogin",
      });
    }

    function handleAccountCreate() {
      modal.open({
        component: "ModalAccountCreate",
      });
    }

    return { handleLogin, handleAccountCreate };
  },
};
</script>

<style lang="postcss" scoped>
main {
  @apply bg-brand-main w-full flex justify-center;
  height: 50%;
}

.blue-balloons {
  background-image: url(../../assets/images/blue_balloons.png);
  background-size: 628px;
  background-position: 90% 100%;
  background-repeat: no-repeat;
}
</style>
