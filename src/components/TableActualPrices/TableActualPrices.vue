<template>
  <div>
    <div class="row mb-3">
      <div class="col-3">
        <v-select class="style-chooser" :clearable="false" v-model="filterProvince" :options=options ></v-select>
      </div>
      <div class="col-auto">
        <select class="d-flex" v-model="fuelType">
          <option value="all">Все виды</option>
          <option v-for="option in fuelTypes" :value=option[0] >{{option[0]}}</option>
        </select>
      </div>
      <div class="col-auto">
        <select class="d-flex" v-model="filterPrice">
          <option value="default">По умолчанию</option>
          <option value="inc">По возростанию</option>
          <option value="dec">По убыванию</option>
        </select>
      </div>
    </div>
    <table class="table table-hover">
      <tbody>
      <ItemTableActualPrices v-for="item in this.data" :key="item.id" :item = "item" />
      </tbody>
    </table>
  </div>
</template>

<script>
  import ItemTableActualPrices from "./ItemTableActualPrices";
  import vSelect from 'vue-select';
  import 'vue-select/dist/vue-select.css';

  function sortByPrice(arr, by, type = 'inc') {
    let sortArray = [];
    let result = [];

    arr.forEach((item) => {
      sortArray.push([item.id, typeof by == "object" ? item[ by[0] ][by[1]] : item[by]])
    });

    sortArray = sortArray.sort(function (a, b) {
      return a[1] - b[1];
    });

    sortArray.forEach((item) => {
      const findItem = arr.filter(el => el.id === item[0]);
      result.push(...findItem);
    });

    if (type === 'dec') return result.reverse();

    return result;
  }

  export default {
    data() {
      return {
        items: [
          {
          "id": "0",
          "place": {
            "city": "Купянск",
            "province": "Киевская"
          },
          "fuelType": "А-95",
          "vendor": ["Россия", "Литва", "Украина"],
          "price": {
            "UAH": "20.65"
          },
          "volume": {
            "min": "2000",
            "max": "40000"
          },
          "time": "1800"
        },
          {
            "id": "1",
            "place": {
              "city": "Николаев",
              "province": "Николаевская"
            },
            "fuelType": "А-92",
            "vendor": ["Кременчуг"],
            "price": {
              "UAH": "19.42"
            },
            "volume": {
              "min": "2000",
              "max": null
            },
            "time": "4200"
          },
          {
            "id": "2",
            "place": {
              "city": "Пролески",
              "province": "Название"
            },
            "fuelType": "ДТ",
            "vendor": ["Италия"],
            "price": {
              "UAH": "20.10"
            },
            "volume": {
              "min": "2000",
              "max": null
            },
            "time": "4555"
          },
          {
            "id": "3",
            "place": {
              "city": "Одесса",
              "province": "Название"
            },
            "fuelType": "А-92",
            "vendor": ["Кременчуг"],
            "price": {
              "UAH": "19.48"
            },
            "volume": {
              "min": "1000",
              "max": null
            },
            "time": "4200"
          },
          {
            "id": "4",
            "place": {
              "city": "Киев",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["НАФТАН"],
            "price": {
              "UAH": "20.20"
            },
            "volume": {
              "min": "2000",
              "max": "400000"
            },
            "time": "4200"
          },
          {
            "id": "5",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Мозир"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4200"
          },
          {
            "id": "6",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Росия"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "8000"
          },
          {
            "id": "7",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "ДТ",
            "vendor": ["Мозир"],
            "price": {
              "UAH": "28.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4200"
          },
          {
            "id": "8",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Украина"],
            "price": {
              "UAH": "26.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4200"
          },
          {
            "id": "9",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Мозир"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4200"
          },
          {
            "id": "10",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Россия"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "6000"
          },
          {
            "id": "11",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Мозир"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4150"
          },
          {
            "id": "12",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "ДТ",
            "vendor": ["Латвия"],
            "price": {
              "UAH": "30.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4200"
          },
          {
            "id": "13",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Мозир"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "3800"
          },
          {
            "id": "14",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-92",
            "vendor": ["Мозир"],
            "price": {
              "UAH": "16.28"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "5500"
          },
          {
            "id": "15",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-95",
            "vendor": ["Украина", "Россия"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4200"
          },
          {
            "id": "16",
            "place": {
              "city": "Город",
              "province": "Название"
            },
            "fuelType": "А-92",
            "vendor": ["Россия"],
            "price": {
              "UAH": "20.15"
            },
            "volume": {
              "min": "3000",
              "max": "32000"
            },
            "time": "4600"
          },
        ],
        fuelType: 'all',
        filterProvince: {
          label: 'Все',
          value: 'all'
        },
        filterPrice: 'default',
        options: [
          { label: 'Все',  value: 'all'},
          { label: 'Киевская',  value: 'Киевская'},
          { label: 'Николаевская',  value: 'Николаевская'},
          { label: 'Название',  value: 'Название'}
          ]
      }
    },
    computed: {
      data() {
        let arr = [];

        switch (this.filterPrice) {
          case "inc":
            arr = sortByPrice(this.items, ['price', 'UAH']);
            break;
          case "dec":
            arr = sortByPrice(this.items, ['price', 'UAH'], 'dec');
            break;
          case "default":
            arr = sortByPrice(this.items, 'time');
            break;
        }

        if(this.fuelType !== 'all')  {
          arr = arr.filter( (item) => {
            return item.fuelType === this.fuelType
          })
        }

        if(this.filterProvince.value !== 'all') {
          arr = arr.filter( (item) => {
            return item.place.province === this.filterProvince.value
          })
        }

        return arr;
      },
      provinces() {
        const map = new Map();
        this.items.forEach( ( { place } ) => map.set(place.province, place.province));
        return map;
      },
      fuelTypes() {
        const map = new Map();
        this.items.forEach(({fuelType}) => map.set(fuelType, fuelType));
        return map;
      }
    },
    components: {
      ItemTableActualPrices,
      "v-select": vSelect
    }
  }
</script>

<style lang="scss">
  .vs__selected {
    color: #fff;
  }
</style>