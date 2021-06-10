<template>
  <div>
    <b-navbar type="faded" variant="light" class="c">
      <b-navbar-brand to="/" class="ml-3">
        <img src="~assets/logoweb1.png" />
      </b-navbar-brand>
	  <b-nav-item>
					{{ $auth.loggedIn }}
				</b-nav-item>
      <b-navbar-brand v-if="$auth.loggedIn" class="ml-auto"> </b-navbar-brand>
      <b-navbar-brand v-b-toggle.sidebar-backdrop href="#" class="ml-auto">
        <img src="~assets/menu1.png" />
      </b-navbar-brand>
    </b-navbar>
  </div>
</template>

<style>
/* import font Kanit */
@import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');
/* import font K2D */
@import url('https://fonts.googleapis.com/css2?family=K2D:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800&display=swap');
img {
  width: 70%;
  height: auto;
}
.c {
  position: fixed;
  /*ทำให้เป็นคนละ layer*/
  z-index: 2;
  height: 70px;
  width: 100%;
}
</style>
