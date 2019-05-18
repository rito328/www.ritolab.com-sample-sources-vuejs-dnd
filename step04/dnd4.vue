<template>
  <div>
    <div id="status">
      <span v-show="status.moving">移動中</span>
      <span v-show="status.fixed">そのアイテムは操作できません</span>
    </div>
    <div>
      <h3>グループA（{{itemsA.length}}）</h3>
      <draggable
        v-model="itemsA"
        group="myGroup"
        :options="options"

        @choose="onChoose"
        @start="onStart"
        @clone="onClone"
        @add="onAdd"
        @remove="onRemove"
        @update="onUpdate"
        @sort="onSort"
        @filter="onFilter"
        @end="onEnd"
      >
        <div class="item" v-for="item in itemsA" :key="item.id" :class="isFixed(item.fixed)">{{item.name}}</div>
      </draggable>
    </div>
    <div>
      <h3>グループB （{{itemsB.length}}）</h3>
      <draggable
        v-model="itemsB"
        group="myGroup"
        :options="options"

        @choose="onChoose"
        @start="onStart"
        @clone="onClone"
        @add="onAdd"
        @remove="onRemove"
        @update="onUpdate"
        @sort="onSort"
        @filter="onFilter"
        @end="onEnd"
      >
        <div class="item" v-for="item in itemsB" :key="item.id" :class="isFixed(item.fixed)">{{item.name}}</div>
      </draggable>
    </div>
    <div>
      <h3>グループC （{{itemsC.length}}）</h3>
      <draggable
        v-model="itemsC"
        group="myGroup"
        :options="options"

        @choose="onChoose"
        @start="onStart"
        @clone="onClone"
        @add="onAdd"
        @remove="onRemove"
        @update="onUpdate"
        @sort="onSort"
        @filter="onFilter"
        @end="onEnd"
      >
        <div class="item" v-for="item in itemsC" :key="item.id" :class="isFixed(item.fixed)">{{item.name}}</div>
      </draggable>
    </div>
  </div>
</template>

<script>
  import draggable from 'vuedraggable'

  export default {
      name: "dnd",

      components: { draggable },

      data () {
          return {
              options: {
                  group: "myGroup",
                  animation: 200,
                  filter: '.fixed'
              },
              itemsA: [
                  { id: 1, name: 'name01', fixed: true },
                  { id: 2, name: 'name02', fixed: false },
                  { id: 3, name: 'name03', fixed: false },
                  { id: 4, name: 'name04', fixed: false },
                  { id: 5, name: 'name05', fixed: false }
              ],
              itemsB: [
                  { id: 6, name: 'name06', fixed: true },
                  { id: 7, name: 'name07', fixed: false },
                  { id: 8, name: 'name08', fixed: false },
                  { id: 9, name: 'name09', fixed: false },
                  { id: 10, name: 'name10', fixed: false }
              ],
              itemsC: [
                  { id: 11, name: 'name11', fixed: true },
                  { id: 12, name: 'name12', fixed: false },
                  { id: 13, name: 'name13', fixed: false },
                  { id: 14, name: 'name14', fixed: false },
                  { id: 15, name: 'name15', fixed: false }
              ],
              status: {
                  moving: false,
                  fixed: false,
              }
          }
      },

      computed: {
          isFixed () {
              return (fixed) => {
                  return {
                      'fixed': fixed === true
                  }
              }
          },
      },

      methods: {
          // フィルタされている要素を選択した時（filterイベント）
          onFilter () {
              console.log('onFilter')
              this.status.fixed = true
              setTimeout(() => {
                  this.status.fixed = false
              }, 1000)

          },
          // 選択された時（chooseイベント）
          onChoose (e) {
              console.log('onChoose')
          },
          // 動作が始まった時（startイベント）
          onStart () {
              console.log('onStart')
              this.status.moving = true;
          },
          // 動作が開始され要素のコピーが行われた時（cloneイベント）
          onClone () {
              console.log('onClone')
          },
          // リストの更新が行われた時（updateイベント）
          onUpdate () {
              console.log('onUpdate')
          },
          // リストに要素が加えられた時（addイベント）
          onAdd () {
              console.log('onAdd')
          },
          // リストから要素が除去された時（removeイベント）
          onRemove () {
              console.log('onRemove')
          },
          // 並び替えが行われた時（sortイベント）
          onSort () {
              console.log('onSort')
          },
          // 動作が終わった時（endイベント）
          onEnd (e) {
              console.log('onEnd')
              this.status.moving = false;
          }
      }
  }
</script>

<style scoped>
  #status {
    min-height: 25px;
    border: 1px solid #42b983;

  }
  .item {
    display: inline-block;
    margin: 10px;
    padding: 10px;
    border: 1px solid #7f7f7f;
    border-radius: 10px;
    background-color: #ffffff;
  }
  .item:hover {
    cursor: grab;
  }
  .item:active {
    cursor: grabbing;
  }
  .sortable-chosen {
    background-color: #42b983;
  }

</style>