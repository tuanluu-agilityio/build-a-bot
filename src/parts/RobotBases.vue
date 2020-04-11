<template>
  <div>
    <h2>Bases</h2>
    The Base is critical to the mobility of your robot. Be
    sure to choose a base that will work well with the terrain
    where your robot needs to operate.
    <div v-for="(base, idx) in bases" :key="idx">
      <h4>{{ base.title }}</h4>
      <img :src="base.src" title="base" alt="" style="width: 200px; height: 200px;" />
      <div>{{ base.description }}</div>
    </div>
  </div>
</template>

<script>
import parts from '../data/parts';

export default {
  name: 'RobotBases',
  data() {
    return { bases: parts.bases };
  },
};
</script>
