<template>
  <div class="home">
    <div class="__wrapper-main-insert-block">
      <div class="card" v-for="(card, i) in dataCard" :key="i">
        <card :card="card"></card>
        <!-- <div class="img showData" v-if="!view" @click.prevent ="viewBlock (i)">
          <img :src="'data:image/svg+xml;base64,' + card.image" alt="image">
        </div>
        <div class="table-results" v-else>
          <div class="_wrapper-block-table">
            <table>
              <thead>
                <tr>
                  <th v-for="(items, i) in headers" :key="i">
                    {{items.title}}
                  </th>
                </tr>
              </thead>
              <tbody>
                  <tr v-for="(td, key) in card.items.slice(0, 5)" :key="key" class="border_bottom">
                    <td>{{td.name}}</td>
                    <td>{{td.level}}</td>
                    <td>{{td.cost}}</td>
                    <td>{{td.chance}}</td>
                  </tr>
              </tbody>
            </table>
          </div>
        </div>
        <div class="card-body">
          <ul>
            <li>
              <strong>{{card.name}}</strong>
              <div class="__li-insert-text">
                <div class="_block-insert-2">
                  <p class="date-text">{{new Date(card.start).toLocaleString('ru-RU',{ year: 'numeric', month: 'numeric', day: 'numeric'}).replace(/[\.\/]/g,'-')}}</p>
                  <strong class="text-uppercase">start</strong>
                </div>
                <div class="_block-insert-2">
                  <p class="date-text">{{new Date(card.end).toLocaleString('ru-RU',{ year: 'numeric', month: 'numeric', day: 'numeric'}).replace(/[\.\/]/g,'-')}}</p>
                  <strong class="text-uppercase">end</strong>
                </div>
              </div>
              <p class="description">{{card.description}}</p>
              <div class="__li-insert-text">
                <div class="_block-insert-2">
                  <p class="bold-text t-blue">{{card.items.length}}</p>
                  <strong class="text-uppercase">items</strong>
                </div>
                <div class="_block-insert-2">
                  <p class="bold-text t-blue">{{card.probability_total}}</p>
                  <strong class="text-uppercase">chancetotal</strong>
                </div>
              </div>
            </li>
          </ul>
        </div>
        <div class="card-actions">
          <button class="btn">Explain</button>
        </div> -->
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import card from '@/components/card.vue'
export default {
  name: 'home',
  components: {
    card
  },
  data: () => ({
    dataCard: [],
    dataTable: []
  }),
  async mounted () {
    const resData = await axios.get('http://localhost:8080/' + 'items.js')
      .then (response=> ( response = response.data))
    let resData1 = resData
    this.dataCard = eval(resData1)
    this.dataTable = this.dataCard
    console.log(this.dataCard)
    console.log(this.dataTable)
  }
}
</script>
