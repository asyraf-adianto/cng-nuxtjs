<template>
    <div class="fixed top-16 h-96 flex w-full px-2 lg:justify-center">
        <form class="bg-white h-96 w-auto px-4 content-start rounded-xl">
            <p class="text-center pt-4 pb-2">Application List</p>
            <a href="#" class="cursor-default h-5/6 mb-4 grid grid-cols-3 overflow-auto">
                <div
                    v-for="menu of api_menu_arr" 
                    :key="menu.id"
                    class="bg-gray-200 h-24 w-24 m-2 rounded-xl hover:bg-indigo-500 item-centered flex justify-center">
                    <NuxtLink :to="{ path: menu.href }" class="cursor-pointer">
                        <p>
                            {{ menu.title }}
                            {{ menu.href }}
                        </p>
                    </NuxtLink>
                </div>
            </a>
        </form>
    </div>
</template>
<script>
  export default {
    head: {
      title: 'My awesome project', // Other meta information
      script: [
        { hid: 'stripe', src: 'https://js.stripe.com/v3/', defer: true },
        { hid: 'jit', src: 'https://unpkg.com/tailwindcss-jit-cdn', defer: true }
      ]
    },
    data() {
      return {
        api_menu_arr:[]
      };
    },
    async fetch() {
        var apps_menu = await fetch('https://opensheet.vercel.app/1S5Sc9J15Rdugl37nkPQmdXhAuHqBjtTyfLZGhu-qmRs/navbar_menu').then(res => res.json())
        this.api_menu_arr = apps_menu
    },
  };
</script>