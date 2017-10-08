<template>
    <div class="destination-list">
        <ol>
            <li v-for="destination in destinations">
                {{ destination.name }}
                <button type="button" class="search-reset" @click="removeDestination(destination)"><span>&times;</span></button>
            </li>
        </ol>
    </div>
</template>

<script>
  export default {
    name: 'destination-list',
    props: ['destinations'],
    methods: {
      removeDestination: function (destination) {
        this.$emit('destination-removed', destination)
      }
    }
  }
</script>

<style scoped>

</style>
