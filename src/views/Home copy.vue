<template>
  <div class="home">
    <div class="__wrapper-main-insert-block">
      <div class="card" v-for="(card, i) in dataCard" :key="i">
        <div class="img showData" v-if="!view" @click.prevent ="viewBlock (i)">
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
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'home',
  data: () => ({
    view: false,
    indexData: null,
    dataCard: [],
    table: [
      {view: false}
    ],
    headers: [
      {title: 'items'},
      {title: 'Level'},
      {title: 'Cost'},
      {title: 'Chance'}
    ],
    dataTable : []
  }),
  methods: {
    viewBlock (i) {
      console.log(i)
    }
  },
  components: {
  },
  async mounted () {
    const resData = await axios.get('http://localhost:8080/' + 'items.js')
    .then(response=> (response = response.data))
    let resData1 = resData
    this.dataCard = eval(resData1)
    this.dataTable = this.dataCard
    console.log(this.dataCard)
    console.log(this.dataTable)
  }
}
</script>
<style>
  body {
    margin: 0;
    padding: 0;
    font-family: 'Roboto', sans-serif;
    font-size: 16px;
  }
  p {
    padding: 0;
    margin: 0;
  }
  .card-actions {
    width: 100%;
  }
  .btn {
    width: 100%;
    background-color: #fff;
    border: 1px solid rgba(0, 0, 0, 0.27);
    border-radius: 5px;
    padding: 10px;
    color: rgba(0, 0, 0, 0.27);
  }
  .home {
    min-height: 100vh;
    width: 100%;
    background-color: gray;
  }
  .__wrapper-main-insert-block {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-around;
    flex-flow: row wrap;
  }
  .card {
    width: 24%;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-flow: row wrap;
    border-radius: 10px;
    background-color: #fff;
    margin: 5px;
  }
  .card .card-body {
    text-align: center;
    padding: 0;
    width: 100%;
  }
  .card .card-actions {
    padding: 10px;
    margin-top: -25px;
  }
  .table-results {
    width: 100%;
    min-height: 100px;
  }
  .img {
    width: 100%;
    position: relative;
  }
  .img img{
    width: 100%;
    height: 300px;
    border-radius: 10px 10px 0 0
  }
  ul {
    padding: 0;
    margin: 0;
  }
  ul li {
    list-style-type: none;
    padding: 15px;
  }
  .date-text {
    color: green;
    font-weight: 600;
  }
  .__li-insert-text {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 5px;
    margin-bottom: 5px;
  }
  ._block-insert-2 {
    padding-right: 20px;
    padding-left: 20px;
  }
  .description {
    color: gray;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    font-size: 0.8rem;
  }
  .text-uppercase {
    text-transform: uppercase;
    font-size: .9rem;
  }
  .t-blue {
    color: blue;
  }
  .bold-text {
    font-weight: 700;
  }
  table {
    width: 100%;
    padding: 10px;
    border-spacing: 0;
  }
  table thead {
    background-color:rgba(128, 128, 128, 0.06);
    padding: 15px;
  }
  table tbody  {
    overflow: scroll;
    height: 100px;
  }
  .border_bottom td {
    border-bottom: 1px solid rgba(128, 128, 128, 0.16);
    height: 30px;
  }
  table tbody tr td {
    font-size: .8rem;
    padding: 5px;
    font-weight: 400;
  }
  table thead tr th {
    border-spacing: 0;
    padding: 0;
    margin: 0;
    padding: 10px;
    font-size: 0.7rem;
    border-bottom: 1px solid #ddd;
  }
</style>
