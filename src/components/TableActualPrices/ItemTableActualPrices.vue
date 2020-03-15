<template>
  <tr>
    <th scope="row">
      <span>{{item.id}} </span>
      <span class="font-weight-bold">{{item.place.city}}</span>
      ({{item.place.province}} обл.)
    </th>
    <td>
      <span class="h6 font-weight-bold">{{item.fuelType}}</span>
    </td>
    <td>
      {{ item.vendor.join(', ') }}
    </td>
    <td> {{ item.price.UAH }} </td>
    <td>
      <span>От {{ item.volume.min }}</span>
      <span v-if="item.volume.max"> - {{ item.volume.min }} л.</span>
    </td>
    <td>
      <a @click.prevent="() => doOrder(item.id)" class="btn btn-primary" href="#">Заказать</a>
    </td>
    <td>Обновление {{Math.floor(item.time)}}</td>
  </tr>
</template>

<script>
  export default {
    props: ['item'],
    methods: {
      doOrder(id) {
        console.log(id);
      }
    }
  }
</script>

<style scoped>
  th, td {
    vertical-align: middle;
  }
</style>