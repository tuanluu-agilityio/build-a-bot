<template>
  <div>
    <h2>Arms</h2>
    The arms are how your robot will interact with the world.
    They come in a variety of shapes and functions.
    <div v-for="(arm, idx) in arms" :key="idx">
      <h4>{{ arm.title }}</h4>
      <img :src="arm.src" title="arm" alt="" style="width: 200px; height: 200px;" />
      <div>{{ arm.description }}</div>
    </div>
  </div>
</template>

<script>
import parts from '../data/parts';

export default {
  name: 'RobotArms',
  data() {
    return { arms: parts.arms };
  },
};
</script>
