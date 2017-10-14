<template>
    <div class="destination-list">
        <div class="location" v-for="(destination, index) in destinations">
            <div class="location__header" @click="selectDestination(destination)">
                <div class="location__dot" :class="{'location__dot--selected': isDestinationSelected(destination)}"></div>
                {{ destination.name }}
            </div>
            <div class="location__description" v-if="isDestinationSelected(destination)">
                <p>
                    Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS. </p>
            </div>
            <div class="location__line" v-if="index !== destinations.length - 1 && !isDestinationSelected(destination)"></div>
        </div>
    </div>
</template>

<script>
  export default {
    name: 'destination-list',
    props: ['destinations'],
    data () {
      return {
        selectedDestination: {}
      }
    },
    methods: {
      selectDestination: function (destination) {
        if (this.isDestinationSelected(destination)) {
          this.selectedDestination = {}
        } else {
          this.selectedDestination = destination
        }
      },
      isDestinationSelected: function (destination) {
        return this.selectedDestination === destination
      },
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
    }

    .location__header {
        padding: 12px 10px 10px 36px;
        cursor: pointer;
    }

    .location__header:hover {
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

    .location__dot--selected {
        background-color: #fff;
    }

    .location__description {
        padding-left: 36px;
    }

    .location__line {
        height: 65%;
        clear: both;
        border-left: 5px solid #acbcc9;
        position: absolute;
        top: 27px;
        left: 17px;
        z-index: 2;
    }
</style>
