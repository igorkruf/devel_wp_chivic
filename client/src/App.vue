<template>
  <div class="body_neksk">
    <q-layout view="lНh lpR fFf">
      <q-header reveal class="hd text-white row justify-between q-pr-md q-gutter-sm">
        <q-btn flat round @click="toggleLeftDrawer" class="q-ml-lg">
          <div class="column justify-between lt-md" style="height: 20px">
            <span class="gm"></span>
            <span class="gm"></span>
            <span class="gm"></span>
          </div>
        </q-btn>

        <q-tabs align="right" class="gt-sm">
          <q-route-tab to="/" label="Главная" />
          <q-route-tab to="/tehnologes" label="Использую" />
          <q-route-tab to="/uslugi" label="Могу" />
        </q-tabs>
      </q-header>
      <q-drawer :breakpoint="4000" show-if-above v-model="leftDrawerOpen" side="left" bordered>
        <q-list>
          <q-item class="my-menu-link" clickable v-ripple to="/" active-class="my-menu-link-act"> Главная</q-item>

          <q-item class="my-menu-link" clickable v-ripple to="/tehnologes" active-class="my-menu-link-act">Использую </q-item>
          <q-item class="my-menu-link" clickable v-ripple to="/uslugi" active-class="my-menu-link-act"> Могу</q-item>
        </q-list>
      </q-drawer>
      <q-page-container>
        <q-page>
          <router-view v-slot="{ Component }">
            <transition name="route_transition" mode="out-in">
              <component :is="Component" />
            </transition>
          </router-view>

          <!-- <router-view /> -->
        </q-page>
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>
import { ref } from 'vue';
//import popup from '@/components/Popup/Popup_service.vue';
export default {
  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      // toggleLeftDrawer() {
      //   leftDrawerOpen.value = !leftDrawerOpen.value;
      // },
    };
  },
  components: {},
};
</script>
<style>
.body_neksk {
  box-sizing: border-box;
  background-color: #d1d1d1fb;
  min-height: 100vh;
}
.q-header {
  background-color: #786964 !important;
}
.q-header > .q-btn {
  width: 48px !important;
  height: 48px !important ;
}
.gm {
  display: block;
  width: 30px;
  height: 2px;
  background-color: #fff;
}

/* анимация переходы

.prozrachnost-enter-active,
.prozrachnost-leave-active {
  transition: opacity 1s;
}

.prozrachnost-enter-from,
.prozrachnost-leave-to {
  opacity: 0;
}
.prozrachnost-enter-to,
.prozrachnost-leave-from {
  opacity: 1;
} */
/* /////////////////////////// */
/* ///////////////////////////// */
/* .prozrachnost_razmer-enter-active,
.prozrachnost_razmer-leave-active {
  transition: opacity 5s linear;
}

.prozrachnost_razmer-enter-from,
.prozrachnost_razmer-leave-to {
  opacity: 0;
}
.prozrachnost_razmer-enter-to,
.prozrachnost_razmer-leave-from {
  opacity: 1;
} */
/* /////////////////////////// */
/* ///////////////////////////// 
.pr-enter-to,
.pr-leave-from {
  opacity: 1;
}
.pr-enter-active,
.pr-leave-active {
  transition: opacity 0.7s ease;
}

.pr-enter-from,
.pr-leave-to {
  opacity: 0;
}

/* /////////////////////////// */
/* ///////////////////////////// */
/* .pr1-enter-to,
.pr1-leave-from {
   opacity: 1; 
  transform: perspective(1800px) rotateY(0deg);
}
.pr1-enter-active,
.pr1-leave-active {
  transition: all 3s ease-in-out;
}

.pr1-enter-from,
.pr1-leave-to {
  opacity: 0;
  transform: perspective(1800px) rotateY(90deg);
} */

/* /////////////////////////// */
/*//////////////////////////////*/
.my-menu-link{
  font-size:16px;
  color:#786964
}

.my-menu-link-act {
  
  background-color: #786964;
  color: white !important;
}
/* Анимация переходов между rout-ами */
.route_transition-enter-active {
  animation: route 0.5s linear;
}

.route_transition-leave-active {
  animation: route 0.5s linear reverse;
}

@keyframes route {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>