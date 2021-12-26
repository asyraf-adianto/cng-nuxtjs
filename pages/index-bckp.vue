<template>
    <div class="fixed inset-x-0 inset-y-2 mt-16 mb-2 mx-4 bg-green-100 flex flex-col">
      <div class="flex-none w-full h-12 mb-2 top-0 bg-red-100 flex items-center">
        <p class="mx-4 font-bold">System Dashboard</p>
        <GeneralButton target="https://opensheet.vercel.app/1S5Sc9J15Rdugl37nkPQmdXhAuHqBjtTyfLZGhu-qmRs/coba2"/>
      </div>
      
      <div class="grow w-full h-full top-0 bg-blue-100">

      </div>
    </div>
</template>

<script>
export default {
  layout (context) {
    return 'WebSystem'
  }
}
</script>
