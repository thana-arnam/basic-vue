<template>
  <section>
    <img v-bind:src="picture" :width="size" :height="size" ref="imageElement" />
    <br />

    <!-- <form v-on:submit.prevent="submitForm">
      <label>ป้อนชื่อเล่น</label>
      <input type="text" ref="nickNameElement"/>
      <button type="submit">บันทึก</button>
    </form> -->

    <h1>ชื่อ-นามสกุล : {{ getFullName }}</h1>
    <!-- <h2>ชื่อเล่น : {{nickName}}</h2> -->
    <h1>อายุ : {{ age }} ปี</h1>
    <h1>เงินเดือน : {{ salary }} บาท</h1>
    <h1>รายได้ต่อปี : {{getIncome}} บาท</h1>
    <h1>ตำแหน่งงาน : {{getDepartment}}</h1>
    <button @click="addSalary(5000)">เพิ่มเงินเดือน</button>
    <!-- <h2>Method 1 : {{getRandomByMethod()}}</h2>
    <h2>Method 2 : {{getRandomByMethod()}}</h2>
    <h2>Method 3 : {{getRandomByMethod()}}</h2>
    <hr/>
    <h2>Computed 1 : {{getRandomByComputed}}</h2>
    <h2>Computed 2 : {{getRandomByComputed}}</h2>
    <h2>Computed 3 : {{getRandomByComputed}}</h2> -->
    <button @click="toggleVisable">{{ isVisable ? "ซ่อน" : "แสดง"}}รายละเอียด</button>
    <article v-show="isVisable">
      <p>ที่อยู่ : <span v-html="address"></span></p>
      <p>Social : <a :href="social" target="_blank">Facebook</a></p>
      <p v-if="hobby.length === 0">ไม่มีงานอดิเรก</p>
      <div v-else>
        <p>งานอดิเรก</p>
        <ul>
          <li v-for="(item, index) in hobby" v-bind:key="index">{{ item }}</li>
        </ul>
      </div>
      <p>ข้อมูลพื้นฐาน</p>
      <ul>
        <!-- <li>เพศ : {{general.gender}}</li>
      <li>น้ำหนัก : {{general.weight}} kg</li>
      <li>ส่วนสูง : {{general.height}} cm</li>
      <li>โรคประจำตัว : {{general.status}}</li> -->
        <li v-for="(item, key) in general" v-bind:key="key">
          {{ key }} : {{ item }}
        </li>
      </ul>
      <!-- <button v-on:click="showData">คลิกเพื่อดูข้อมูล 1</button>
    <button @click="showData">คลิกเพื่อดูข้อมูล 2</button>
    <button @click="increment(10)">เพิ่ม</button>
    <button @click.ctrl="increment(3)">เพิ่ม click mouse ซ้ายและกด control</button>
    <button @click="decrement(5)">ลด</button>
    <button @click.right="decrement(2)">ลด click mouse ขวา</button>
    <button @click.middle="decrement(1)">ลด click mouse กลาง</button> -->
    </article>
  </section>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: "Thanamat",
      lastName: "Arnamwat",
      nickName: "",
      age: 28,
      address: "<strong>กรุงเทพมหานคร</strong>",
      picture: "https://cdn-icons-png.flaticon.com/512/3135/3135715.png",
      size: 150,
      social: "https://www.facebook.com/kongruksiamtutorial",
      hobby: ["ทำสวน", "เล่นเกมส์", "ฟังเพลง", "อ่านหนังสือ"],
      general: {
        gender: "หญิง",
        weight: 42.3,
        height: 150,
        status: false,
      },
      isVisable: false,
      salary: 20000
    };
  },
  methods: {
    // getFullName() {
    //   return `${this.firstName} ${this.lastName}`;
    // },
    showData() {
      alert(this.firstName);
    },
    increment(value) {
      this.age += value;
    },
    decrement(value) {
      this.age -= value;
    },
    setNickName(event) {
      this.nickName = event.target.value;
    },
    submitForm() {
      this.nickName = this.$refs.nickNameElement.value;
    },
    toggleVisable() {
      this.isVisable = !this.isVisable
    },
    getRandomByMethod() {
      return Math.random();
    },
    addSalary(value) {
      this.salary+=value;
    }
  },
  computed: {
    getFullName() {
      return `${this.firstName} ${this.lastName}`;
    },
    getRandomByComputed() {
      return Math.random();
    },
    getIncome() {
      return this.salary * 12;
    },
    getDepartment() {
      return this.salary >= 35000 ? "Project Manager" : "Programmer";
    }
  }
};
</script>

<style></style>
