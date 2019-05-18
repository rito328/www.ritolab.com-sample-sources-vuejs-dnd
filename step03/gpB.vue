<template>
  <div>
    <h3>グループB</h3>
    <draggable v-model="itemsB" group="myGroup" @start="drag=true" @end="drag=false" :options="options">
      <div class="item" v-for="item in itemsB" :key="item.id">{{item.name}}</div>
    </draggable>
  </div>
</template>

<script>
    import draggable from 'vuedraggable'

    export default {
        name: "gpB",

        components: { draggable },

        data () {
            return {
                options: {
                    group: "myGroup",
                    animation: 200
                },
                itemsB: [
                    { id: 6, name: 'name06' },
                    { id: 7, name: 'name07' },
                    { id: 8, name: 'name08' },
                    { id: 9, name: 'name09' },
                    { id: 10, name: 'name10' }
                ]
            }
        }
    }
</script>
