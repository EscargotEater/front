<template>
  <div>
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
          <b-nav-item to="/"><p class="a">หน้าแรก</p></b-nav-item>
          <!-- b-nav-item ไม่มี property style color -->

          <b-nav-item to="/aboutus"><p class="a">เกี่ยวกับเรา</p></b-nav-item>

          <b-nav-item v-if="$auth.loggedIn" to="/profile"
            ><p class="a">ข้อมูลสมาชิก</p></b-nav-item
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
                <b-nav-item to="/detectdiabetes"
                  ><p class="f">โรคเบาหวาน</p></b-nav-item
                >
                <b-nav-item to="/detectheart"
                  ><p class="f">โรคหัวใจ</p></b-nav-item
                >
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>

          <b-nav-item v-if="$auth.loggedIn" to="/history"
            ><p class="f">ประวัติการตรวจ</p></b-nav-item
          >

          <b-navbar toggleable type="dark">
            <b-navbar-brand href="#"><p class="e">ข้อมูลโรค</p></b-navbar-brand>
            <b-navbar-toggle target="navbar-toggle-collapse2" class="d">
            </b-navbar-toggle>
            <!-- id ยังไม่ได้ใช้ -->
            <b-collapse id="navbar-toggle-collapse2" is-nav>
              <b-navbar-nav class="g">
                <b-nav-item to="/diabetesinfo"
                  ><p class="f">ข้อมูลโรคเบาหวาน</p></b-nav-item
                >
                <b-nav-item to="/heartinfo"
                  ><p class="f">ข้อมูลโรคหัวใจ</p></b-nav-item
                >
              </b-navbar-nav>
            </b-collapse>
          </b-navbar>

          <b-nav-item to="/game"><p class="a">เกมส์ตอบคำถาม</p></b-nav-item>
          <b-nav-item v-if="!$auth.loggedIn" to="/login"
            ><p class="a">เข้าสู่ระบบ</p></b-nav-item
          >
          <b-nav-item v-if="!$auth.loggedIn" to="/register"
            ><p class="a">ลงทะเบียน</p></b-nav-item
          >
          <b-nav-item v-if="$auth.loggedIn" @click="logOut"
            ><p class="a">ออกจากระบบ</p></b-nav-item
          >
        </b-nav>
      </div>
    </b-sidebar>
  </div>
</template>