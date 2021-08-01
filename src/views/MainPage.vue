<template>
  <div class="container-div">
    <!-- Cover Image -->
    <div class="cover-img">
      <v-img
        src="../assets/indian-food-curry-butter-chicken-palak-paneer-chiken-tikka-biryani-vegetable-curry-papad-dal-palak-sabji-jira-alu-rice-138549925.jpeg"
        alt="food-image"
        class="img"
      ></v-img>
    </div>
    <!-- Image && Tabs  -->
    <div class="tabs-cont px-10 d-flex align-center">
      <div class="d-flex align-center" style="column-gap: 1.5rem">
        <img
          src="../assets/tim_mcbaj_53652000_2255623191378916_4966133143083590398_n@2x.png"
          class="img"
        />
        <p class="primary-color cursor-pointer">Show Card</p>
      </div>
      <v-spacer></v-spacer>
      <div class="tabs d-flex">
        <h4
          class="rounded-pill py-2 px-4 mx-8"
          :class="label === currentTab && 'selected'"
          v-for="(label, i) in ['Portfolio', 'Availability', 'Pricing Package']"
          :key="i"
          @click="currentTab = label"
        >
          {{ label }}
        </h4>
      </div>
      <v-spacer></v-spacer>
      <v-spacer></v-spacer>
    </div>
    <!-- Pricing package table -->
    <table class="w-100 pricing mt-10" v-if="currentTab === 'Pricing Package'">
      <tbody>
        <tr class="header">
          <th>title</th>
          <th>Category</th>
          <th>Items</th>
          <th>Date Created</th>
          <th>Amount</th>
        </tr>
        <tr class="t-data">
          <td>Wedding Classic</td>
          <td>Wedding</td>
          <td>15</td>
          <td>5th Sep, 2020</td>
          <td>N350, 000</td>
        </tr>
      </tbody>
    </table>

    <!--  Availability-->
    <div class="calender" v-if="currentTab === 'Availability'">
      <div class="availability-container">
        <v-date-picker
          v-model="dates"
          color="#ffaa0a"
          full-width
          range
          class="mt-4 custom-calender"
          :weekday-format="getDay"
          :first-day-of-week="0"
        ></v-date-picker>
        <div class="booking">
          <div class="d-flex align-baseline pl-8">
            <div class="rounded-circle small-circle"></div>
            <p class="pl-8 primary-color mt-10">Booked</p>
            <p class="pl-8 light-text">Orange shaded dates are booked days</p>
          </div>
          <div class="d-flex align-baseline pl-8">
            <div class="rounded-circle small-circle-unshaded"></div>
            <p class="pl-8 primary-color mt-4">Available</p>
            <p class="pl-8  light-text">Unshaded days are free days</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MainPage',
  data() {
    return {
      currentTab: 'Portfolio',
      dates: ['2021-04-10', '2021-04-20'],
    };
  },
  methods: {
    getDay(date) {
      const daysOfWeek = ['Sun', 'Mon', 'Tue', 'Wed', 'Thur', 'Fri', 'Sat'];
      let i = new Date(date).getDay(date);
      return daysOfWeek[i];
    },
  },
};
</script>

<style lang="scss">
@import '../styles/variables.scss';
body {
  background-color: $background-color;
}

.container-div {
  padding: 1rem 1.5rem 1rem 1.2rem;
  .cover-img {
    height: 10rem;

    .img {
      border-radius: 10px;
      height: inherit;
    }
  }

  .tabs-cont {
    position: relative;
    margin-top: 2rem;
    .img {
      width: 3rem;
      position: relative;
    }
    .tabs {
      h4 {
        font-size: 16px/25px;
        color: $almost-black;
        font-weight: 400;
        cursor: pointer;
      }
      .selected {
        background-color: #ffdeb75f;
        font-weight: 600;
      }
    }
  }
  table.pricing {
    margin-top: 2rem;
    .header {
      background-color: $highlighted-color;
      border-radius: 4px;
      th {
        padding: 8px 0;
        font-weight: 500;
      }
    }
    .t-data {
      td {
        padding: 12px 0;
        text-align: center;
      }
    }
  }
}
.availability-container {
  margin-left: auto;
  margin-right: auto;
  width: fit-content;

  .custom-calender {
    .v-picker__title {
      display: none !important;
    }
    .v-date-picker-table {
      width: 500px;
      margin-left: auto;
      margin-right: auto;
    }
    .v-date-picker-header {
      width: 700px;
      margin-left: auto;
      margin-right: auto;

      button {
        font-size: 16px/25px !important;
        color: $almost-black !important;
        font-weight: 400 !important;
      }
      .v-btn.v-btn--icon {
        position: relative !important;
        top: 12rem !important;
        background-color: #ebebeb;
      }
    }
    .v-date-picker-table--date th {
      border-bottom: solid 1px #dad5d5 !important;
      border-top: solid 1px #dad5d5 !important;
    }
    tbody {
      position: relative;
      top: 2rem;
      transition: none !important;
      td {
        button {
          margin-bottom: 10px !important;
        }
      }
    }
    thead {
      th {
        font-size: 16px/25px !important;
        color: $almost-black !important;
        font-weight: 400 !important;
      }
    }
  }
  .small-circle {
    background: $primary-color;
    height: 10px;
    width: 10px;
  }
  .small-circle-unshaded {
    background: #ebebeb;
    height: 10px;
    width: 10px;
  }
}
</style>
