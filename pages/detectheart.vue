<template>
  <div class="o">
    <p class="b">แบบฟอร์มประเมินความเสี่ยงการเป็นโรคเบาหวาน</p>
    <hr class="solid" />
    <b-container fluid>
      <b-card
        border-variant="primary"
        header="โปรดกรอกข้อมูลผลตรวจสุขภาพประจำปี"
        header-bg-variant="primary"
        header-text-variant="white"
        bg-variant="light"
        body-class="text-center"
        align="center"
        style="
          color: darkslategray;
          font-family: 'K2D', sans-serif;
          font-size: 22px;
          margin-top: 50px;
        "
      >
        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> อายุ </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="age"
              v-model="value.age"
              inline
              min="0"
              max="200"
              size="lg"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> ปี </b-card-text>
          </b-col>
        </b-row>

        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> ระดับน้ำตาลในเลือด </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="glucose"
              v-model="value.glucose"
              inline
              min="0"
              max="500"
              size="lg"
              step="0.1"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> มิลลิลิตร/เดซิลิตร </b-card-text>
          </b-col>
        </b-row>

        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> ความยาวรอบเอว </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="waist"
              v-model="value.waist"
              inline
              min="0"
              max="300"
              size="lg"
              step="0.1"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> เซนติเมตร </b-card-text>
          </b-col>
        </b-row>

        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> ความดันสูงสุดขณะหัวใจบีบตัว </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="pressurehigh"
              v-model="value.pressurehigh"
              inline
              min="0"
              max="250"
              size="lg"
              step="0.1"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> มิลลิเมตร.ปรอท </b-card-text>
          </b-col>
        </b-row>

        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> ความดันต่ำสุดขณะหัวใจคลายตัว </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="pressurelow"
              v-model="value.pressurelow"
              inline
              min="0"
              max="250"
              size="lg"
              step="0.1"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> มิลลิเมตร.ปรอท </b-card-text>
          </b-col>
        </b-row>

        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> คลอเรสเตอรอลทั้งหมด </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="chloresterolall"
              v-model="value.chloresterolall"
              inline
              min="0"
              max="250"
              size="lg"
              step="0.1"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> มิลลิกรัม.เดซิลิตร </b-card-text>
          </b-col>
        </b-row>

        <b-row class="mb-3" align-v="center">
          <b-col>
            <b-card-text> คลอเรสเตอรอลHDL </b-card-text>
          </b-col>
          <b-col cols="2">
            <b-form-spinbutton
              id="hdl"
              v-model="value.hdl"
              inline
              min="0"
              max="150"
              size="lg"
              step="0.1"
            ></b-form-spinbutton>
          </b-col>
          <b-col>
            <b-card-text> มิลลิกรัม.เดซิลิตร </b-card-text>
          </b-col>
        </b-row>
      </b-card>
    </b-container>

    <b-button
      type="submit"
      size="lg"
      variant="primary"
      align="center"
      style="
        margin-left: 37%;
        margin-top: 50px;
        font-family: 'K2D', sans-serif;
        font-size: 25px;
      "
      >ประเมินความเสี่ยง
    </b-button>
  </div>
</template>

<script>
export default {
  layout: 'headerguest',
  data() {
    return {
      value: {
        age: 50,
        glucose: 100,
        waist: 70,
        pressurehigh: 120,
        pressurelow: 80,
        chloresterolall: 175,
        hdl: 50,
      },
    }
  },
  methods: {
    onSubmit2(event) {
      event.preventDefault()
      alert(JSON.stringify(this.value))
    },
  },
}
</script>

<style>
/* import font Kanit */
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
/* import font K2D */
@import url('https://fonts.googleapis.com/css2?family=K2D:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');

.o {
  margin-left: 300px;
  margin-right: 300px;
  padding-left: 50px;
  padding-right: 50px;
  padding-bottom: 50px;
}

.b {
  color: darkslategray;
  font-family: 'K2D', sans-serif;
  font-size: 40px;
  text-align: center;
  padding-top: 150px;
}

.h {
  margin-top: 50px;
  background-color: rgb(226, 226, 226);
  padding-left: 20px;
  padding-right: 20px;
  padding-bottom: 20px;
  border-style: ridge;
  border-width: 3px;
}

.i {
  background-color: rgb(255, 255, 255);
  padding-top: 30px;
  margin-top: 20px;
  border-style: outset;
}

.j {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 150px;
  margin-right: 150px;
  margin-bottom: 30px;
}

.k {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 140px;
  margin-right: 130px;
  margin-bottom: 30px;
}

.l {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 140px;
  margin-right: 125px;
  margin-bottom: 30px;
}

.m {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 80px;
  margin-right: 90px;
  margin-bottom: 30px;
}

.n {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 100px;
  margin-right: 100px;
  margin-bottom: 30px;
}

.p {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 55px;
  margin-right: 55px;
  margin-bottom: 30px;
}

.q {
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  margin-left: 95px;
  margin-right: 95px;
  margin-bottom: 30px;
}

hr.solid {
  border-top: 1px solid #bbb;
}
</style>
