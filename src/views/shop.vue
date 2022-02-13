<template  >
  <v-container >
    
    <center><h1 class="text-info">Shop Doraemon</h1></center>
    <v-container class="d-flex flex-wrap">
      <v-card
        class="mx-auto mb-5"
        max-width="400"
        v-for="(i, index) in productlist"
        :key="index"
      >
        <v-img class="black--text align-end" height="200px" :src="i.imageurl">
          <v-card-title>{{ i.name }}</v-card-title>
        </v-img>

        <v-card-subtitle class="pb-0">{{ i.rightText }}</v-card-subtitle>

        <v-card-text class="text--primary">
          <div>{{ i.leftText }}</div>
        </v-card-text>

        <v-card-actions>
          <v-btn color="teal lighten-1" text :to="'/detail/' + i.name">detail</v-btn>
          <v-btn color="deep-orange lighten-2" text > Add </v-btn>
          <div class="card-footer">
            <input type="checkbox" class="form-control" @change="selected(i)" />
          </div>
        </v-card-actions>
      </v-card>
    </v-container>

    <table class="table table-striped table-hover">        
    
    </table>
    <v-container
      ><h4 class="text-danger fs-1">ยอดชำระเงิน  {{ total() }} บาท</h4></v-container
    >
    <v-container grid-list-xs class="light-blue accent-1">
      <router-view :key="$route.path"></router-view>
    </v-container>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
        productlist: [
        {
         
          name: "ของวิเศษโดราเอมอน - ประตูไปที่ไหนก็ได้",
          imageurl:
            "data:image/jpeg;base64,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",
          rightText: "จะได้ใช้เดินทางไปไหนต่อไหนได้สะดวกและรวดเร็ว อีกทั้งยังเป็นของวิเศษที่มีปัญหาน้อยที่สุดด้วย",
          ctaText: "Shop Now",
          active: false,
          price: 15000000000,
        },

        {
         
          name: "ของวิเศษโดราเอมอน - ขนมปังช่วยจำ",
          imageurl:
            "https://pbs.twimg.com/media/Cn6GtcfUMAAGmhU.jpg",
          rightText: "ขนมปังที่โนบิตะใช้แปะลงหนังสือแล้วกิน เพื่อให้จำข้อสอบได้ก่อนไปสอบ เป็นของวิเศษอีกชนิดที่น่าจะมีประโยชน์ในชีวิตจริง เพื่อป้องกันอาการหลงๆลืมๆ",
          ctaText: "Shop Now",
          active: false,
          price: 1000000000,
        },

        {
         
          name: "ของวิเศษโดราเอมอน - วุ้นแปลภาษา",
          imageurl:
            "http://f.ptcdn.info/604/026/000/1418734622-d6f57faf76-o.jpg",
          rightText: "เป็นของวิเศษที่อยากได้ในชีวิตจริงอีกอย่าง เพราะเวลาคุยกับคนต่างชาติจะได้ไม่มีปัญหา",
          ctaText: "Shop Now",
          active: false,
          price: 1500000000,
        },

        {
         
          name: "ของวิเศษโดราเอมอน - ไทม์แมชชีน",
          imageurl:
            "https://www.beautyhunter.co.th/wp-content/uploads/2017/01/x360-7Jy.jpg",
          rightText: "สุดยอดของวิเศษจากอนาคตที่โผล่มาตั้งแต่ตอนแรกของเรื่อง",
          ctaText: "Shop Now",
          active: false,
          price: 999999999999,
        },
      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
 
};
</script>

<style>
h2 {
  color: rgb(255, 56, 139);
}
</style>
