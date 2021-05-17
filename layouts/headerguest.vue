<template>
  <div>
    <div class="c">
      <b-navbar type="faded" variant="light">
        <b-navbar-brand href="http://127.0.0.1:3000/home" class="ml-3">
          <img src="../assets/logoweb1.png" />
        </b-navbar-brand>
        <b-navbar-brand v-b-toggle.sidebar-backdrop href="#" class="ml-auto">
          <img src="../assets/menu1.png" />
        </b-navbar-brand>
      </b-navbar>
    </div>
    <b-sidebar
      id="sidebar-backdrop"
      bg-variant="primary"
      text-variant="light"
      backdrop
      right
      shadow="lg"
    >
      <div class="px-3 py-2">
        <b-nav vertical>
          <b-nav-item href="http://127.0.0.1:3000/home"
            ><p class="a">หน้าแรก</p></b-nav-item
          >
          <!-- b-nav-item ไม่มี property style color -->

          <b-nav-item href="http://127.0.0.1:3000/aboutus"
            ><p class="a">เกี่ยวกับเรา</p></b-nav-item
          >

          <b-navbar toggleable type="dark">
            <b-navbar-brand href="#"
              ><p class="e">ประเมินโรค</p></b-navbar-brand
            >
            <b-navbar-toggle target="navbar-toggle-collapse1" class="d">
            </b-navbar-toggle>
            <!-- id ยังไม่ได้ใช้ -->
            <b-collapse id="navbar-toggle-collapse1" is-nav>
              <b-navbar-nav class="g">
                <b-nav-item href="http://127.0.0.1:3000/detectdiabetes"
                  ><p class="f">โรคเบาหวาน</p></b-nav-item
                >
                <b-nav-item href="http://127.0.0.1:3000/detectheart"
                  ><p class="f">โรคหัวใจ</p></b-nav-item
                >
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>

          <b-navbar toggleable type="dark">
            <b-navbar-brand href="#"><p class="e">ข้อมูลโรค</p></b-navbar-brand>
            <b-navbar-toggle target="navbar-toggle-collapse2" class="d">
            </b-navbar-toggle>
            <!-- id ยังไม่ได้ใช้ -->
            <b-collapse id="navbar-toggle-collapse2" is-nav>
              <b-navbar-nav class="g">
                <b-nav-item href="http://127.0.0.1:3000/diabetesinfo"
                  ><p class="f">ข้อมูลโรคเบาหวาน</p></b-nav-item
                >
                <b-nav-item href="http://127.0.0.1:3000/heartinfo"
                  ><p class="f">ข้อมูลโรคหัวใจ</p></b-nav-item
                >
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>

          <b-nav-item href="http://127.0.0.1:3000/game"
            ><p class="a">เกมส์ตอบคำถาม</p></b-nav-item
          >
          <b-nav-item href="http://127.0.0.1:3000/login"
            ><p class="a">เข้าสู่ระบบ</p></b-nav-item
          >
          <b-nav-item href="http://127.0.0.1:3000/register"
            ><p class="a">ลงทะเบียน</p></b-nav-item
          >
        </b-nav>
      </div>
    </b-sidebar>
    <Nuxt />
  </div>
</template>

<script>
export default {}
</script>

<style>
/* import font Kanit */
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
/* import font K2D */
@import url('https://fonts.googleapis.com/css2?family=K2D:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');
img {
  width: 70%;
  height: auto;
}
.a {
  color: white;
  font-family: 'K2D', sans-serif;
  font-size: 25px;
}

.a:hover {
  border-left-color: solid white;
  padding-left: 15px;
  border-width: 4px;
}

.b {
  color: white;
  font-family: 'K2D', sans-serif;
  font-size: 25px;
}
.c {
  position: fixed;
  /*ทำให้เป็นคนละ layer*/
  z-index: 2;
  height: 70px;
  width: 100%;
}

/*adjust dropdown button */
.d {
  margin-bottom: 15px;
  border-width: 5px;
}

.e {
  color: white;
  font-family: 'K2D', sans-serif;
  font-size: 25px;
}

.f {
  color: dodgerblue;
  font-family: 'K2D', sans-serif;
  font-size: 25px;
  padding-left: 20px;
  margin-top: 12px;
}

.f:hover {
  border-left: solid dodgerblue;
  padding-left: 10px;
  border-width: 4px;
  margin-left: 15px;
  margin-top: 12px;
}

.g {
  background-color: white;
  margin-right: 10px;
}

.h {
  height: 50px;
}

.header {
  height: 70px;
  width: 100%;
}
</style>
