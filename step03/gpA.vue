<template>
  <div>
    <h3>グループA</h3>
    <draggable v-model="itemsA" group="myGroup" @start="drag=true" @end="drag=false" :options="options">
      <div class="item" v-for="item in itemsA" :key="item.id">{{item.name}}</div>
    </draggable>
  </div>
</template>

<script>
    import draggable from 'vuedraggable'

    export default {
        name: "gpA",

        components: { draggable },

        data () {
            return {
                options: {
                    group: "myGroup",
                    animation: 200
                },
                itemsA: [
                    { id: 1, name: 'name01' },
                    { id: 2, name: 'name02' },
                    { id: 3, name: 'name03' },
                    { id: 4, name: 'name04' },
                    { id: 5, name: 'name05' }
                ]
            }
        }
    }
</script>
