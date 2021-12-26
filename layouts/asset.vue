<template>
    <container class="relative bg-gray-100 w-screen h-screen">
        <header class="z-50 fixed top-0 flex flex-row gap-4 justify-between items-center content-center w-full h-12 px-10 border-b border-gray-300">
            <HeaderLogoLeft class="w-2/5"/>
            <HeaderMenuCenter :list="[{'href':'/','title':'Home'}]" class="w-1/5"/>
            <HeaderUserRight class="w-2/5"/>
        </header>
        <body class="flex flex-col justify-between items-center content-center h-screen w-screen">
            <div class="h-12 w-screen bg-transparent"></div>
            <Nuxt />
            <div class="h-7 w-screen bg-transparent"></div>
        </body>
        <footer class="z-50 fixed bottom-0 flex flex-row gap-4 justify-center items-center content-center text-gray-400 bg-blue-200 w-full h-7">
            <p class="text-sm">All right reserved</p>
        </footer>
    </container>
</template>
<script>
    export default {
        
    }
</script>