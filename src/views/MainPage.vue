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

    <div class="relative" v-if="show">
      <!-- POP Up -->
      <div class="pop-up" transition="scale-transition">
        <div class="hide">
          <p
            class="primary-color float-right pr-7 cursor-pointer"
            @click="show = !show"
          >
            Hide
          </p>
        </div>
        <div class="relative mt-10">
          <div class="d-flex justify-center">
            <img
              src="../assets/tim_mcbaj_53652000_2255623191378916_4966133143083590398_n@2x.png"
              class="img-pop"
            />
          </div>
          <h3>Ekemini Mark</h3>
          <p class="description">
            I’m a wedding and portrait photographer based in Lagos, Nigeria.
            I’ve been shooting weddings since I was in high school (before I
            ever had my driver’s license!).
          </p>
          <v-row justify="center mt-1">
            <v-col cols="4">
              <p class="text-center">22.1k</p>
              <p class="text-center">Total View</p>
            </v-col>
            <v-col cols="4">
              <p class="text-center">22.1k</p>
              <p class="text-center">Total View</p>
            </v-col>
            <v-col cols="4">
              <p class="text-center">22.1k</p>
              <p class="text-center">Total View</p>
            </v-col>
          </v-row>
          <div class="d-flex mt-3">
            <!-- <div> -->
            <span style="color: #4D4D4D;opacity: 0.6;">Category</span>
            <ul class="d-flex" style="column-gap:30px">
              <li>Food</li>
              <li>Food</li>
              <li>Food</li>
              <li>Food</li>
            </ul>
            <!-- </div> -->
          </div>
          <div class="d-flex mt-2">
            <span style="color: #4D4D4D;opacity: 0.6;">Location</span>
            <p class="pl-5">Lagos, Nigeria</p>
          </div>
          <div class="link d-flex justify-center mt-16">
            <v-icon
              color="#F29F05"
              size="15"
              class="pr-3"
              style="transform:rotate(180deg}"
              >mdi-share-variant-outline</v-icon
            >
            <p>www.peexoo.ai/anijohnson</p>
          </div>
          <div
            class="link d-flex justify-center mt-5 align-center"
            style="column-gap: 7px;"
          >
            <v-btn icon color="black">
              <v-icon size="20">mdi-heart</v-icon>
            </v-btn>
            <v-btn icon color="black">
              <v-icon size="20">mdi-heart</v-icon>
            </v-btn>
            <v-btn icon color="black">
              <v-icon size="20">mdi-heart</v-icon>
            </v-btn>
            <v-btn depressed class="rounded-pill btn-primary" color="#ffaa0a"
              >Book Now</v-btn
            >
          </div>
          <div class="d-flex pl-10 justify-center mt-10">
            <p style="color:#4D4D4D">Built</p>
            <v-icon
              color="#F29F05"
              size="15"
              class="px-1"
              style="transform:rotate(180deg}"
              >mdi-heart</v-icon
            >
            <p style="color:#4D4D4D">on Peexoo</p>
          </div>
        </div>
      </div>
    </div>
    <!-- Image && Tabs  -->
    <div :style="show && 'padding-left: 20rem'">
      <div class="tabs-cont px-10 d-flex align-center">
        <div
          class="d-flex align-center"
          style="column-gap: 1.5rem"
          v-if="!show"
        >
          <img
            src="../assets/tim_mcbaj_53652000_2255623191378916_4966133143083590398_n@2x.png"
            class="img"
          />
          <p class="primary-color cursor-pointer" @click="show = !show">
            Show Card
          </p>
        </div>
        <v-spacer></v-spacer>
        <div class="tabs d-flex">
          <h4
            class="rounded-pill py-2 px-4 mx-8"
            :class="label === currentTab && 'selected'"
            v-for="(label, i) in [
              'Portfolio',
              'Availability',
              'Pricing Package',
            ]"
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
      <table
        :class="show ? 'table-hide pricing' : 'w-100 pricing mt-10'"
        v-if="currentTab === 'Pricing Package'"
      >
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
          <tr class="t-data">
            <td>Wedding Classic</td>
            <td>Wedding</td>
            <td>15</td>
            <td>5th Sep, 2020</td>
            <td>N350, 000</td>
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

      <!-- images -->
      <div
        class="d-flex mt-8"
        v-if="currentTab === 'Portfolio'"
        :style="show && 'padding-left: 20rem'"
        style="flex-flow:row wrap;grid-gap:0.8rem "
      >
        <img
          src="../assets/indian-food-curry-butter-chicken-palak-paneer-chiken-tikka-biryani-vegetable-curry-papad-dal-palak-sabji-jira-alu-rice-138549925.jpeg"
          alt=""
          v-for="(card, i) in 10"
          :key="i"
          style="height:13rem;object-fit: contain;border-radius:10px"
          :style="
            show
              ? `width:18rem; height:13rem;object-fit: contain;border-radius:10px`
              : 'width:19rem'
          "
        />
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
      show: false,
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
  padding: 1rem 1.5rem 2rem 1.2rem;
  background-color: $background-color;
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
    background-color: $background-color;
    .v-picker__title {
      display: none !important;
    }
    .v-picker__body {
      background-color: $background-color;
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
.pop-up {
  width: 26rem;
  height: fit-content;
  position: absolute;
  margin-left: 6rem;
  z-index: 5;
  top: 8rem;
  background: white;
  padding: 15px;
  border: 0.25px solid #ffb500;
  border-radius: 4px;
  //   .img-pop {
  //     width: 2rem;
  //     height: 2rem;
  //   }
  h3 {
    font-size: 1.7rem;
    font-weight: 600;
    color: #000000;
    text-align: center;
    padding: 0.8rem 0;
  }
  .description {
    font-size: 1rem;
    // font-weight: 300;
    color: #000000;
    text-align: center;
    padding: 0 1.5rem;
    letter-spacing: -0.26px;
  }
}
.hide {
  position: absolute;
  right: 0;
}
.table-hide {
  margin-left: auto;
  width: 80%;
}
.image-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-gap: 0 20px;
  grid-auto-rows: 10px;
}
.image-list img {
  width: 250px;
  grid-row-end: span 2;
}
</style>
