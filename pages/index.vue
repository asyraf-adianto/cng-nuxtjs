<template>
    <div class=" grid grid-rows-4 grid-flow-col gap-4 p-4 h-full w-full" >
      <div class="col-span-4 bg-blue-400">Test</div>
      <div class="row-span-3 col-span-4 bg-blue-400">Test2</div>
    </div>
</template>
<script>
export default {
  layout (context) {
    return 'asset'
  }
}
</script>