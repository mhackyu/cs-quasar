<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title>
          Music Library
        </q-toolbar-title>

        <div>Made with 💖 by <a href="https://github.com/mhackyu" target="_blank" style="color: white; text-decoration: none;">mhackyu</a></div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-grey-2"
    >
      <q-list>
        <q-item-label header>App</q-item-label>
        <q-item clickable tag="a" to="/">
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Home</q-item-label>
            <q-item-label caption>Music Library</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" to="/login">
          <q-item-section avatar>
            <q-icon name="assignment_ind" />
          </q-item-section>
          <q-item-section>
            <q-item-label>Login</q-item-label>
            <q-item-label caption>Login Now</q-item-label>
          </q-item-section>
        </q-item>
        <q-item-label header>Technology Stacks</q-item-label>
        <q-item clickable tag="a" target="_blank" href="https://vuejs.org/">
          <q-item-section avatar>
            <img src="https://vuejs.org/images/logo.png" height="24px"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Vue</q-item-label>
            <q-item-label caption>vuejs.org</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" href="https://quasar.dev/">
          <q-item-section avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg" height="27px"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Quasar</q-item-label>
            <q-item-label caption>quasar.dev</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" href="https://firebase.google.com/">
          <q-item-section avatar>
            <img src="https://www.gstatic.com/mobilesdk/160503_mobilesdk/logo/2x/firebase_28dp.png" height="27px"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Firebase</q-item-label>
            <q-item-label caption>firebase.google.com</q-item-label>
          </q-item-section>
        </q-item>
        <q-item clickable tag="a" target="_blank" href="https://socket.io/">
          <q-item-section avatar>
            <img src="https://mpng.pngfly.com/20180825/veg/kisspng-socket-io-node-js-javascript-network-socket-websoc-socket-io-logo-in-svg-jpg-png-5b81a6e505cd53.3223084015352235250238.jpg" height="22px"/>
          </q-item-section>
          <q-item-section>
            <q-item-label>Socket.IO</q-item-label>
            <q-item-label caption>socket.io</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
export default {
  name: 'MyLayout',

  data () {
    return {
      leftDrawerOpen: false
    }
  }
}
</script>
