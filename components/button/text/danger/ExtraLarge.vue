<template>
    <button 
        class="flex flex-row items-center content-center justify-center  
        h-14 px-6 py-2  text-xl
        text-red-500 active:text-red-700 focus:text-red-600" >
        <div class="fas pr-1" :class="this.icon"></div>
        <p class="">{{ this.text }}</p>
    </button>
</template>
<script>
    export default {
        head: {
            script: [
                { hid: "alpine", src: "//unpkg.com/alpinejs", defer: true }
            ]  
        },
        props: {
            text: {
                type: String,
                default: "Button"
            },
            icon: {
                type: String,
                default: "hidden !pr-0"
            },
        },
    }
</script>