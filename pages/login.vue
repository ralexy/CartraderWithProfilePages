<template>
  <div class="mt-10">
    <h1 class="text-5xl font-bold mb-7">
      Log In
    </h1>
    <button class="bg-red-400 hover:bg-red-700 text-white font-bold p-3 rounded" @click="login">
      Log In with Google
    </button>

    <div v-if="user !== null">
      <!-- Affichez d'autres informations de l'utilisateur selon votre besoin -->
    </div>
  </div>
</template>

<script setup>  
definePageMeta({
  layout: 'custom',
});

const supabase = useSupabaseClient();
const user = useSupabaseUser();


const login = async () => {
  const {error} = supabase.auth.signInWithOAuth({
    provider: 'google',
  });

  if(error) { console.log(error); }
  else { navigateTo('/'); }
};
</script>
