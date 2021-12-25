<template>
    <div class="flex flex-col justify-center gap-2 h-fit w-fit">
        <button type="Standard" 
            class="flex flex-row items-center content-center justify-center 
            h-6 px-2 py-1 rounded-xl text-sm !text-white active:text-gray-100 
            active:ring-0 focus:ring-offset-2 focus:ring 
            bg-blue-500 active:bg-blue-700 focus:ring-blue-300">
            <div class="fas pr-1" :class="this.icon"></div>
            <p class="">{{ this.text }}</p>
        </button>
    </div>
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