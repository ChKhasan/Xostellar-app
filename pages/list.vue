<template>
  <div class="master">
    <SiteTop :title="title" />

    <div class="container">
      <div class="tabler">
        <table>
          <tr>
            <th>{{ $store.state.translations["registry_num"] }}</th>
            <th>{{ $store.state.translations["hostel_name"] }}</th>
            <th>{{ $store.state.translations["hostel_region"] }}</th>
            <th>{{ $store.state.translations["address"] }}</th>
            <th>{{ $store.state.translations["hostel_status"] }}</th>
            <th>{{ $store.state.translations["hostel_phone"] }}</th>
          </tr>
          <tr v-for="item in hotels?.data" :key="item.id">
            <td>
              <p class="strong">{{ item?.register_number || "—" }}</p>
            </td>
            <td>
              <p class="strong">{{ item.name }}</p>
            </td>
            <td>
              <p class="weak">{{ item.region.name }}</p>
            </td>
            <td>
              <p class="weak">
                {{ item.address }}
              </p>
            </td>
            <td>
              <span v-if="item?.deregistration_date !== null" class="status passive"
                >{{ $store.state.translations["register_out"] }}</span
              >
              <span v-else>
                <p v-show="item.status == 1" class="status active">
                  {{ $store.state.translations["active"] }}
                </p>
                <p v-show="item.status == 0" class="status passive">
                  {{ $store.state.translations["passive"] }}
                </p>
              </span>
            </td>
            <td>
              <NuxtLink :to="localePath(`/hotels/${item.id}`)">
                <p class="num">
                  {{ item.phone_number }}

                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="20"
                    height="20"
                    viewBox="0 0 20 20"
                    fill="none"
                  >
                    <path
                      d="M10.5521 6.71083L13.8413 9.99999L10.5521 13.2892M6.17625 9.99999H13.8313M17.7771 9.99999C17.7771 14.2963 14.2942 17.7792 9.99792 17.7792C5.7016 17.7792 2.21875 14.2963 2.21875 9.99999C2.21875 5.70368 5.7016 2.22083 9.99792 2.22083C14.2942 2.22083 17.7771 5.70368 17.7771 9.99999Z"
                      stroke="#00B55D"
                      stroke-miterlimit="10"
                      stroke-linecap="round"
                      stroke-linejoin="round"
                    />
                  </svg>
                </p>
              </NuxtLink>
            </td>
          </tr>
        </table>
      </div>

      <PaginationElement @getData="__GET_HOTELS" :totalPage="totalPage" v-if="totalPage > 20" />
    </div>
  </div>
</template>

<script>
import hotelsApi from "@/api/hotels";

export default {
  data() {
    return {
      title: this.$store.state.translations["list_title"],
      hotels: [],
      totalPage: 1,
    };
  },

  async mounted() {
    this.__GET_HOTELS();
  },
  methods: {
    async __GET_HOTELS() {
      try {
        const hotels = await hotelsApi.getHotels(this.$axios, {
          params: { page: 1, ...this.$route.query },
          headers: {
            Authorization: `Bearer ${localStorage.getItem("authToken")}`,
          },
        });

        this.hotels = hotels;
        this.totalPage = hotels.total;
      } catch (e) {}
    },
  },
};
</script>

<style scoped>
@import url(@/assets/css/table.css);
.container {
  margin: 40px auto 112px auto;
}
@media screen and (max-width: 1024px) {
  .container {
    margin: 40px 0;
    overflow: hidden;
  }
}
</style>
