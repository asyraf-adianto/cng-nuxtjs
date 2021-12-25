<template>
    <div class="flex flex-col justify-center gap-2 h-fit w-fit">
        <button  
            class="flex flex-row items-center content-center justify-center  
            h-8 px-2 py-1 rounded-xl text-sm border-2 active:ring-0 
            focus:ring-offset-2 focus:ring
            border-red-500 text-red-500 active:border-red-700 
            active:text-red-700 active:bg-red-50 focus:ring-red-300">
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