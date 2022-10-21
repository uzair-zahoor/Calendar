<template>
  <div class="cal">
    <!-- <h2>Inside from Calendar</h2> -->
    <!-- <div class="head">{{ getday }}</div> -->
    <div class="head">
      <button @click="prev" @keydown="pre">&lt;</button>
      <h2 class="h-date">{{ date }} {{ getmonth }} {{ year }}</h2>
      <button @click="next" @keydown="nxt">&gt;</button>
    </div>
    <div class="body">
      <div class="days">
        <div class="subhead" v-for="d in days" :key="d">
          <div class="day">{{ d }}</div>
        </div>
      </div>
      <div class="date">
        <div class="values" v-for="d in firstDay" :key="d">
          <div class="value">{{}}</div>
        </div>
        <div class="values" v-for="value in lastDate" :key="value">
          <div :class="{ active: value == date }" class="value">
            {{ value }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
let today = new Date();
// today.setDate(12);
export default {
  name: "CalendarCom",
  data() {
    return {
      today: today.getDay(),
      date: today.getDate(),
      month: today.getMonth(),
      year: today.getFullYear(),
      values: [],
      months: [
        "January",
        "February",
        "March",
        "April",
        "May",
        "June",
        "Jully",
        "August",
        "September",
        "October",
        "November",
        "Decemember",
      ],
      days: ["Sun", "Mon", "Tues", "Wed", "Thur", "Fri", "Sat"],
    };
  },
  methods: {
    next() {
      if (this.month == 11) {
        this.month = 0;
        this.year += 1;
      } else {
        this.month = this.month + 1;
      }
      this.lastDate;
    },
    prev() {
      if (this.month == 0) {
        this.month = 11;
        this.year -= 1;
      } else {
        this.month = this.month - 1;
      }
      this.lastDate;
    },
    nxt(e) {
      if (e.keyCode == 39) {
        this.next();
      }
    },
    pre(e) {
      if (e.keyCode == 37) {
        this.prev();
      }
    },
  },
  created() {
    console.log(new Date(this.year, this.month, 1).getDay());
  },
  computed: {
    lastDate() {
      return new Date(this.year, this.month + 1, 0).getDate();
    },
    firstDay() {
      return new Date(this.year, this.month, 1).getDay();
    },
    getmonth() {
      return this.months[this.month];
    },
    getday() {
      return this.days[this.today];
    },
  },
};
</script>
<style scoped>
.active {
  background-color: rgb(72, 73, 73);
  color: rgb(223, 223, 223);
}
.cal {
  background-color: rgb(229, 226, 226);
  width: 555px;
  padding: 1px;
  margin: auto;
  border-radius: 5px;
  overflow: hidden;
  /* border: 1px solid gray; */
  box-shadow: 5px 5px 5px gray;
}
.head {
  width: 100%;
  height: 70px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px;
  /* border-bottom: 1px solid gray; */
}
.h-date {
  color: gray;
}
.head button {
  width: 50px;
  outline: none;
  border: none;
  color: rgb(71, 70, 70);
  font-size: 30px;
  background-color: transparent;
}

.days {
  margin: 3px 0px;
  display: flex;
  justify-content: center;
  justify-content: center;
  align-items: center;
  height: 50px;
  background-color: rgb(72, 73, 73);
  border-radius: 10px;
  color: rgb(223, 223, 223);
}
.day {
  width: 79px;
}
.date {
  display: flex;
  flex-wrap: wrap;
}
.value {
  border: 1px solid rgb(138, 137, 137);
  border-radius: 20%;
  box-shadow: 2px 2px 2px gray;
  width: 77px;
  height: 70px;
  /* background-color: rgb(138, 137, 137); */
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 1px 1px;
}
</style>
