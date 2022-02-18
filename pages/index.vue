<template>
  <div
    class="flex gap-3 absolute top-0 bottom-0 right-0 left-0 flex-col justify-center items-center bg-gradient-to-r from-sky-500 to-red-400"
  >
    <div>
      <img class="drop-shadow-xl" src="/favicon.ico" alt="nuxt logo" />
    </div>
    <div v-if="this.$auth.user" class="flex items-center gap-3 bg-white rounded-xl px-3 py-2">
        <div>
            <img class="w-12 h-12 rounded-full" :src="this.$auth.user.picture" alt="">
        </div>
        <div class="flex flex-col">
            <div>{{this.$auth.user.username}}</div>
            <div>exp {{new Date(this.$auth.user.exp*1000).toLocaleString("th-TH")}}</div>
        </div>
        <div @click="$auth.logout()" class="bg-red-500 hover:bg-red-600 px-3 py-1 text-white rounded-xl cursor-pointer select-none">
            Sign Out
        </div>
    </div>
    <div class="text-3xl text-white">
      Count : {{ this.$store.state.counter }}
    </div>
    <div class="flex gap-2">
      <div
        @click="$store.commit('increase')"
        class="py-2 px-3 bg-sky-500 hover:bg-sky-600 rounded-xl text-white cursor-pointer select-none"
      >
        Increase
      </div>
      <div
        @click="$store.commit('decrease')"
        class="py-2 px-3 bg-sky-500 hover:bg-sky-600 rounded-xl text-white cursor-pointer select-none"
      >
        Decrease
      </div>
      <NuxtLink
        to="/login"
        class="py-2 px-3 bg-sky-500 hover:bg-sky-600 rounded-xl text-white cursor-pointer select-none"
      >
        Login
      </NuxtLink>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
    // methods: {
    //   increase() {
    //     this.$store.commit('increase')
    //   },
    // },
}
</script>
