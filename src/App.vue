<template>
<div
  @click="showRadialMenu"
  style="height: 100%; width: 100%; position: relative"
>
  <div
    v-if="!menuHidden"
    class="menu-item"
    :style="{ top: horisontalMenuY, left: leftMenux }"
  >
    burger
  </div>
  <div
    v-if="!menuHidden"
    class="menu-item"
    :style="{ top: horisontalMenuY, left: rightMenux }"
    @click.stop="pizzaAlert"
  >
    pizza
  </div>
  <div
    v-if="!menuHidden"
    class="menu-item"
    :style="{ top: topMenuY, left: verticalMenuX }"
   
  >
    pasta
  </div>
  <div
    v-if="!menuHidden"
    class="menu-item"
    :style="{ top: bottomMenuY, left: verticalMenuX }"
    @click.stop="sushiAlert"
  >
    sushi
  </div>
</div>
</template>

<script>
import { ref } from 'vue';

export default {
setup() {
  const radius = 100;
  const menuHidden = ref(true); // Initially hidden
  const leftMenux = ref('0px');
  const rightMenux = ref('0px');
  const horisontalMenuY = ref('0px');
  const topMenuY = ref('0px');
  const bottomMenuY = ref('0px');
  const verticalMenuX = ref('0px');

  function pizzaAlert(event) {
    alert('Mamma mia!');
  }

  function sushiAlert(event) {
    alert('Irasshaimase!');
  }

  function showRadialMenu(event) {
    if (menuHidden.value) {
      const mouseX = event.clientX;
      const mouseY = event.clientY;

      leftMenux.value = `${mouseX - radius - 25}px`;
      rightMenux.value = `${mouseX + radius - 25}px`;
      horisontalMenuY.value = `${mouseY - 25}px`;
      topMenuY.value = `${mouseY + radius - 25}px`;
      bottomMenuY.value = `${mouseY - radius - 25}px`;
      verticalMenuX.value = `${mouseX - 25}px`;

      menuHidden.value = false; // Show the menu
    } else {
      menuHidden.value = true; // Hide the menu
    }
  }

  return {
    menuHidden,
    leftMenux,
    rightMenux,
    horisontalMenuY,
    showRadialMenu,
    topMenuY,
    bottomMenuY,
    verticalMenuX,
    pizzaAlert,
    sushiAlert,
    pastaAlert,
  };
},
};
</script>
