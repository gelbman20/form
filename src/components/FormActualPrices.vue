<template>
  <TableActualPrices />
</template>

<script>
  import TableActualPrices from "./TableActualPrices";
  export default {
    components: {
      TableActualPrices
    }
  }
</script>

<!--
{
	"products": [
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
	]
}
-->