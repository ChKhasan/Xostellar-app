<template>
  <div class="wrap">
    <div class="">
      <div class="cardo">
        <img
          v-if="$store.state.imageShow"
          src="@/assets/img/vector.png"
          class="vector"
          alt=""
        />
        <h4 class="title">{{ $store.state.translations["main_title"] }}</h4>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.wrap {
  /* margin-top: 24px; */
}
.cardo {
  background: url(@/assets/img/hero-2.jpg) center no-repeat;
  background-size: cover;
  /* border-radius: 32px; */
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 440px;
}
.cardo::after {
  content: "";
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background: #0201056f;
  /* border-radius: 32px; */
}
.vector {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 2;
}
.title {
  color: var(--White, var(--White, #fff));
  text-align: center;
  font-size: var(--48);
  font-style: normal;
  font-weight: 600;
  line-height: 120%;
  position: relative;
  z-index: 8;
  max-width: 745px;
  letter-spacing: 1px;
}
@media screen and (max-width: 1024px) {
  .cardo {
    border-radius: 20px;
    min-height: 238px;
  }
  .cardo::after {
    border-radius: 20px;
  }
  .title {
    max-width: 90%;
    margin: 0 auto;
    font-size: var(--24);
    font-style: normal;
    font-weight: 600;
    line-height: 130%;
  }
  .vector {
    width: 95px;
    height: 95px;
  }
}
</style>
