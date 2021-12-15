<template>
  <div class="fixed top-0 w-full ">
        <nav class="h-14 flex bg-white items-center justify-between p-4 z-40">
            <div class="navbar-menu hidden lg:order-1 lg:block w-full lg:w-2/5">
                <ul>
                    <li v-for="menu of api_submenu_arr" :key="menu.id" class="block lg:inline-block mt-4 lg:mt-0 mr-10 text-blue-900 hover:text-indigo-600">
                        <NuxtLink :to="{ path: menu.href }"> 
                            <p>{{ menu.title }}</p>
                        </NuxtLink>
                    </li>
                </ul>
            </div>
            <div class="navbar-menu hidden lg:order-3 lg:block w-full lg:w-2/5 lg:text-right">
                <a class="block lg:inline-block mt-4 lg:mt-0 text-blue-900 hover:text-indigo-600" href="#">
                    Contact
                </a>
            </div>
            <div class="block lg:hidden">
                <button class="navbar-burger flex items-center py-2 px-3 text-indigo-500 rounded border border-indigo-500">
                    <svg class="fill-current h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                        <title>
                            Menu
                        </title>
                        <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z">
                        </path>
                    </svg>
                </button>
            </div>
            <label style="font-family: 'Baloo Tamma 2'" class="select-none text-xl mx-1 cursor-pointer h-10 border px-4 px-1 border-indigo-100 rounded-full lg:order-2 mx-1 flex flex-row items-center">
              <div v-if="$fetchState.pending" class="flex flex-row items-center">
                <img v-if="$fetchState.pending" class="inset-0 animate-spin h-8 items-center" src="https://www.svgrepo.com/show/381093/ball-game-poke-sport-sports.svg" alt="logo-chronus-favicon" border="0">
              </div>
              <div v-else class="flex flex-row items-center">
                <img  class="inset-0 h-8 items-center" src="https://www.svgrepo.com/show/381093/ball-game-poke-sport-sports.svg" alt="logo-chronus-favicon" border="0">
                <p class="pl-3">{{ this.api_menu_obj.title_lc }}</p>
              </div>
              <input type="checkbox" name="show_more" id="show_more" class="hidden peer"/>
              <div class="transition duration-300 ease-out fixed inset-0 opacity-0 invisible peer-checked:visible mt-14 min-h-screen w-full bg-black peer-checked:opacity-50 -z-50">
              </div>
              <div class="transition duration-300 ease-out fixed inset-0 opacity-0 invisible peer-checked:visible peer-checked:opacity-100">
                <GeneralNavMenu />
              </div>
            </label>
        </nav>
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
        api_menu_obj:[],
        api_submenu_arr:[],
        user: {
          "username":"asyraf.adianto@gmail.com",
          "name":"Asyraf Nur"
        }
      };
    },
    async fetch() {
        var apps_menu = await fetch('https://opensheet.vercel.app/1S5Sc9J15Rdugl37nkPQmdXhAuHqBjtTyfLZGhu-qmRs/navbar_menu').then(res => res.json())
        this.api_menu_obj = apps_menu.filter(function(d) { return d.title_lc == "system" } )[0]
        const navbar_menu_id = this.api_menu_obj.id
        var apps_submenu = await fetch('https://opensheet.vercel.app/1S5Sc9J15Rdugl37nkPQmdXhAuHqBjtTyfLZGhu-qmRs/navbar_submenu').then(res => res.json())
        this.api_submenu_arr = apps_submenu.filter(function(a) { return a.navbar_menu_id == navbar_menu_id })
    },
  };
</script>
<style>
  @import "https://fonts.googleapis.com/css?family=Source+Sans+Pro:wght@200|Baloo+Tamma+2|Roboto&display=swap";
</style>