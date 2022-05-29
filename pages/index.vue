<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          โปรแกรมคำนวณการซื้อของที่ร้านค้า
        </v-card-title>
        <v-card-text>
          <v-text-field
            v-model="money"
            label="เงินที่มีอยู่"
            type="number"
          ></v-text-field>
          <div>{{ calculationResult }}</div>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      money: 0,
    };
  },
  computed: {
    calculationShop1() {
      let money = this.money;
      let price = 25;
      let qty = 0;
      let total = 0;
      qty = money / price;
      if (qty >= 10) {
        price = 20;
      }
      total = money / price;

      return parseInt(total);
    },
    calculationShop2() {
      let money = this.money;
      let price = 30;
      let qty = 0;
      let total = 0;
      qty = money / price;
      for (let i = 0; i <= qty; i++) {
        if (i > 1 && i % 3 == 0) {
          ++qty;
        }
      }

      total = qty;

      return parseInt(total);
    },
    calculationResult() {
      let result = "";
      let shop1 = this.calculationShop1;
      let shop2 = this.calculationShop2;
      if (this.money) {
        if (shop1 > shop2) {
          result = "แนะนำร้านที่ 1";
        } else {
          result = "แนะนำร้านที่ 2";
        }
      }

      return result;
    },
  },
};
</script>
