<template>
    <div class="flex items-center justify-center">
        {{ results.status }}
    </div>
</template>
<script>
    export default {
        props: {
            target: {
                type: String,
                default: "https://opensheet.vercel.app/1S5Sc9J15Rdugl37nkPQmdXhAuHqBjtTyfLZGhu-qmRs/coba1"
            }
        },
        data() {
            return {
                results: {
                    "status": "loading.."
                }
            };
        },
        async fetch() {
            var get_result = await fetch(this.target).then(res => res.json())
            this.results = get_result[0]    
        },
    }
</script>