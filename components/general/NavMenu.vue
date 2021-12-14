<template>
    <div class="fixed top-16 h-96 flex w-full px-2 lg:justify-center">
        <form class="bg-white h-96 w-auto px-4 content-start rounded-xl">
            <p class="text-center pt-4 pb-2">Application List</p>
            <div class="h-5/6 mb-4 grid grid-cols-3 overflow-auto">
                <div class="cursor-pointer bg-gray-200 h-24 w-24 m-2 rounded-xl hover:bg-indigo-500 item-centered flex justify-center">
                    <a href="/">
                        Dashboard
                    </a>
                </div>
                <div class="cursor-pointer bg-gray-200 h-24 w-24 m-2 rounded-xl hover:bg-indigo-500 item-centered flex justify-center">
                    <a href="/asset">
                        Asset
                    </a>
                </div>
            </div>
        </form>
    </div>
</template>