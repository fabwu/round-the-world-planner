<template>
    <div class="destination-list">
        <div class="location" v-for="(destination, index) in destinations">
            <div class="location__dot"></div>
            {{ destination.name }}
            <div class="location__line" :class="{ hidden: index === destinations.length - 1 }"></div>
        </div>
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
    .destination-list {
        height: 100%;
    }

    .location {
        position: relative;
        padding: 12px 10px 10px 36px;
        cursor: pointer;
    }

    .location:hover {
        background-color: #f8f8f8;
    }

    .location__dot {
        width: 15px;
        height: 15px;
        border-radius: 50%;
        border: 2px solid #acbcc9;
        background-color: #acbcc9;
        position: absolute;
        left: 12px;
        top: 13px;
    }

    .location__line {
        height: 70%;
        clear: both;
        border-left: 5px solid #acbcc9;
        position: absolute;
        top: 27px;
        left: 17px;
        z-index: 2;
    }
</style>
