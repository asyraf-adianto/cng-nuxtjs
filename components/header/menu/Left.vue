<template>
    <div class="flex flex-row gap-2 justify-start items-center content-center h-10">
        <NuxtLink v-for="menu of this.list" :key="menu.href" :to="menu.href" >
            <ButtonTextOptionalSmall :text="menu.title" class="font-bold"/>
        </NuxtLink>
    </div>
</template>
<script>
export default {
    props: {
        list: {
            type: Array,
            default: [
                {
                    "href":"/component-test",
                    "title":"Home"
                },
                {
                    "href":"/component-test/backup",
                    "title":"Backup"
                }
            ]
        }
    },
    data() {
        return {
            config: {

            }
        }
    },
    methods: {
    }
}
</script>