<template>
  <div class="">
    <h1>候補日選択</h1>
    <ul>
      <li
        v-for="(item, index) in CandidateDate"
        :key="'list-item' + index"
        class="item"
      >
      <p class="item_title">候補日{{ index + 1 }}
        <input v-if="(CandidateDate.length > 1)" type="button" @click="deleteItem(index)" class="Dbtn" value="x">
      </p>
      <p>日付を選択</p>
      <input type="date" v-model="item.date">
      <p>開始時間を選択</p>
      <input type="time" v-model="item.start">
      <p>終了時間を選択</p>
      <input type="time" v-model="item.end">
      </li>
    </ul>
    <input type="button" @click="additem" value="候補日を追加">
    <table border="1">
      <tr>
        <th>date</th><th>start</th><th>end</th>
      </tr>
      <tr
      v-for="(item, index) in CandidateDate"
      :key="'list-item' + index"
      >
        <td>{{item.date}}</td><td>{{item.start}}</td><td>{{item.end}}</td>
      </tr>
    </table>
  </div>
</template>

<script>

export default {
  name: 'home',
  data () {
    return {
      CandidateDate: [
        {
          date: '',
          start: '',
          end: ''
        }
      ]
    }
  },
  methods: {
    additem () {
      this.CandidateDate.push({
        date: '',
        startTime: '',
        endTime: ''
      })
      /*
      this.$nextTick(() => {
        let list = document.getElementById('candidate-list')
        console.log(list)
        list.scrollTop = list.scrollHeight
      }) */
    },
    deleteItem (index) {
      this.CandidateDate.splice(index, 1)
    }
  }
}
</script>

<style media="screen">
.item{
  margin: 5px auto;
  border: solid 2px rgb(83, 148, 154);
}
.item_title{
  font-weight: bold;
  text-align: left;
  height: 50px;
  font-size: 30px;
  width: 100%;
  margin-top: 0;
  color: rgb(255, 255, 255);
  background-color: rgb(83, 148, 154);
}
ul {
  list-style: none;
  overflow: auto;
  max-height: 320px;
  max-width: 500px;
  width: 50%;
  margin: auto;
}
.Dbtn{
  float: right;
  width: 50px;
  height: 50px;
  font-size: 20px;
}
</style>
