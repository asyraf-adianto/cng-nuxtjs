<template>
    <div class="flex flex-col justify-center gap-2 h-fit w-fit">
        <button 
            class="flex flex-row items-center content-center justify-center  
            h-8 px-2 py-1 rounded-xl text-sm
            text-gray-500 active:text-gray-700 focus:text-gray-600" >
            <div class="fas pr-1" :class="this.icon"></div>
            <p class="underline">{{ this.text }}</p>
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