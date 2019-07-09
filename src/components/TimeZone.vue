<template>
  <div class="box">
    <h1 class="title">world clock</h1>
    <ul>
      <li 
        v-for="timeZone in timeZoneList"
        :key="timeZone.city"
      >
        <div class="date">
          <p>
            {{ timeZone.city }}
          </p>
          <p>
            {{ timeZone.date }} {{ timeZone.month }} {{ timeZone.year }}
          </p>
        </div>
        <div class="time">
          {{ timeZone.time }}
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
const timeZones = [
  { id: 'new york', name: 'America/New_York' },
  { id: 'london', name: 'Europe/London' },
  { id: 'bangkok', name: 'Asia/Bangkok' },
  { id: 'taiwan', name: 'Asia/Taipei' },
  { id: 'sydney', name: 'Australia/Sydney' }
];
export default {
  name: 'TimeZone',
  data() {
    return {
      timer: null,
      timeZoneList: []
    }
  },
  methods: {
    getLocaleTime() {

      this.timeZoneList = timeZones.map((timeZone) => {

        const localeDate = new Date().toLocaleString('en-us', { 
          hour12: false, 
          timeZone: timeZone.name,
          year: 'numeric',
          month: 'short',
          day: '2-digit',
          hour: '2-digit',
          minute: '2-digit',
        });

        return {
          city: timeZone.id,
          year: localeDate.split(',')[1].trim(),
          month: localeDate.split(',')[0].split(' ')[0].trim(),
          date: localeDate.split(',')[0].split(' ')[1].trim(),
          time: localeDate.split(',')[2].trim()
        }

      });

    }
  },
  mounted() {
    this.timer = setInterval(() => {
      this.getLocaleTime();
    }, 1000);
  },
  destroyed() {
    
    if (this.timer) {
      clearInterval((this.timer));
      this.timer = null;
    }

  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.box {
  margin: 0 auto;
  text-transform: uppercase;
  padding: 72px 15px;
}
.title {
  margin: 0 0 30px 0;
  border-top: 10px solid black; 
  border-bottom: 10px solid black; 
  font-size: 40px;
  text-align: center;
  font-weight: 800;
}
ul {
  margin: 0;
  border-right: 2px solid #000000;
  border-left: 2px solid #000000;
  padding: 0;
  list-style: none;
  li {
    display: flex;
    align-items: center;
    border-bottom: 2px solid #000000;
    padding: 14px 20px;
    background-color: #ffffff;
    & > div {
      flex: 1;
    }
    p {
      margin: 0;
    }
    &:first-child,
    &:last-child {
      background-color: #000000;
      color: white;
    }
  }
}
.date {
  p {
    font-weight: bold;
  }
  p:nth-child(1) {
    font-size: 24px;
  }
  p:nth-child(2) {
    font-size: 16px;
    font-style: italic;
    margin: 5px 0;
  }
}
.time {
  font-size: 40px;
  font-weight: bold;
  text-align: right;
}
@media screen and (min-width: 767px) {
  .box {
    max-width: 540px;
  }
  .title {
    font-size: 65px;
    white-space: nowrap;
  }
  ul li {
    padding: 16px 40px;
  }
  .time {
    font-size: 72px;
    font-weight: bold;
  }
  .date {
    p:nth-child(1) {
      font-size: 36px;
    }
  }
}
</style>
