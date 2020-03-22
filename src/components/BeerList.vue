<template>
  <div>
    <li
      v-for="name in results.response.beers.items"
      :key="name.first_checkin_id"
    >{{ name.beer.beer_name }} - {{ name.brewery.brewery_name }}</li>
  </div>
</template>

<script>
import axios from "axios"
const Axios = axios.create({
  baseURL:
    "https://api.untappd.com/v4/user/beers/ajtruex/?access_token=794D4BD1989F28A6AE1BF16538B43050783CF73C"
})
const apiKey = "794D4BD1989F28A6AE1BF16538B43050783CF73C"

Axios.defaults.headers.common = { Authorization: `Bearer` + apiKey }
// export const HTTP = axios.create({
//   baseURL: `https://api.untappd.com/v4`,
//   headers: {
//     Authorization: "Bearer 794D4BD1989F28A6AE1BF16538B43050783CF73C"
//   }
// })
// axios
//   .get("https://api.untappd.com/v4/user/beers/ajtruex/?sort=highest_rated", {
//     headers: {
//       Authorization: `Bearer 794D4BD1989F28A6AE1BF16538B43050783CF73C`
//     }
//   })
//   .then(function(response) {
//     console.log(response)
//   })
// axios
//   .get("https://api.coindesk.com/v1/bpi/currentprice.json")
//   .then(response => (this.info = response))
//   .then(function(response) {
//     console.log(response)
//   })
export default {
  data() {
    return {
      info: "",
      results: []
      // beers: []
    }
  },
  created() {
    axios
      .get(
        "https://api.untappd.com/v4/user/beers/ajtruex/?access_token=794D4BD1989F28A6AE1BF16538B43050783CF73C"
      )
      .then(response => {
        this.results = response.data
      })
  }
  // created() {
  //   axios
  //     .get("http://api.untappd.com/v4/user/beers/ajtruex/?sort=highest_rated", {
  //       headers: {
  //         Authorization: `Bearer 794D4BD1989F28A6AE1BF16538B43050783CF73C`
  //       }
  //     })
  //     .then(response => (this.info = response))
  // },
  // mounted() {
  //   axios
  //     .get("https://api.coindesk.com/v1/bpi/currentprice.json")
  //     .then(response => (this.info = response.data.bpi))
  // },
  // filters: {
  //   currencydecimal(value) {
  //     return value.toFixed(2)
  //   }
  // }
}
</script>

<style></style>
