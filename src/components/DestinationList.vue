<template>
    <div class="destination-list">
        <ul>
            <li v-for="destination in destinations">{{ destination.name }}</li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'destination-list',
    props: ['destinations']
  }
</script>

<style scoped>

</style>
