<template>
  <div class="wraper-card-components">
    <div class="img showData" v-if="!visible" @click.prevent ="visible =!visible">
      <img :src="'data:image/svg+xml;base64,' + card.image" alt="image" class="image-bg">
      <img src="https://www.stickees.com/files/love/gifts/458-yellow-and-red-gift-box.png" class="img-main-bg">
    </div>
    <div class="table-results" v-else @click.prevent ="visible =!visible">
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
</template>
<script>
export default {
  props: ['card'],
  data: () => ({
    visible: false,
    headers: [
      { title: 'items' },
      { title: 'Level' },
      { title: 'Cost' },
      { title: 'Chance' }
    ],
  }),
  methods: {
    viewBlock (i) {
      console.log(i)
    }
  }
}
</script>
