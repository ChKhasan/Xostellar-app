<template>
  <div class="wrap">
    <div class="container small">
      <div class="left">
        <h4 class="title">{{ $store.state.translations["main_title"] }}</h4>
        <p class="txt">
          Аxborot tizimi orqali qogʼoz hujjat aylanishi kamayadi, reyestrdan koʼchirma berish toliq elektron shaklda amalga oshiriladi, ishchi jarayonga sarflanadigan vaqt bir necha barobariga qisqartirish imkonini beradi.
        </p>
        <p class="second">
          Ushbu axborot tizimi yordamida quyidagi jarayonlar raqamlashtiriladi:
         <ul>
         <li>
         
– Xostellar, oʼtovli va chodirli oromgohlar Reyestri, shuningdek har bir xostel, oʼtovli va chodirli oromgohlar kerakli maʼlumotlari bilan toʼldirilgan yagona maʼlumotlar bazasini shakllantirish;

         </li>
         <li>
          – Oʼzbekiston Respublikasi hududida faoliyat yuritayotgan xostellar, oʼtovli va chodirli oromgohlar reyestrini yuritish;

         </li>
         <li>
          – qoʼmita tomonidan xostellar, oʼtovli va chodirli oromgohlar faoliyati nazoratini yuritish;
         </li>
         <li>
– statistik maʼlumotlarni yuritish.
         
         </li>
         </ul>
        </p>
      </div>
      <div class="right">
        <img src="@/assets/img/about.png" alt="" class="pic" />
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.wrap {
  padding: 64px 0;
}
.container {
  display: grid;
  align-items: center;
  grid-template-columns: repeat(2, 1fr);
}
.title {
  color: var(--Blue-dark, #002856);
  font-size: 32px;
  font-style: normal;
  font-weight: 600;
  line-height: 120%; /* 38.4px */
  margin-bottom: 24px;
  max-width: 380px;
  font-family: var(--medium);
}
.txt {
  color: var(--Black, #020105);
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 150%; /* 24px */
  margin-bottom: 20px;
}
.second {
  color: var(--Black, #020105);
  font-size: 16px;
  font-style: normal;
  font-weight: 400;
  line-height: 150%; /* 24px */
  padding-left: 8px;
  border-left: 4px solid #00B55D;
}
.pic {
  width: 100%;
}
@media screen and (max-width: 1024px) {
  .wrap {
    padding: 0;
  }
  .container {
    padding: 40px 24px;
    display: block;
  }
  .title {
    font-size: 20px;
    font-style: normal;
    font-weight: 600;
    line-height: 140%;
    margin-bottom: 24px;
    max-width: 60%;
  }
}
</style>
