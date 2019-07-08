<template>
  <div class="box">
    <h1 class="title">world clock</h1>
    <ul>
      <li>
        <div class="date">
          <p>new york</p>
          <p>27 JAN 2019</p>
        </div>
        <div class="time">02:46</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'TimeZone',
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
  padding: 0;
  list-style: none;
  li {
    display: flex;
    align-items: center;
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
