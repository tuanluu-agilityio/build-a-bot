<template>
  <div>
    <h2>Toros</h2>
    The torso is the central part of your robot that holds everything
    together. Choosing the right torso will help ensure your robot
    functions well with the parts you choose.
    <div v-for="(torso, idx) in torsos" :key="idx">
      <h4>{{ torso.title }}</h4>
      <img :src="torso.src" title="torso" alt="" style="width: 200px; height: 200px;" />
      <div>{{ torso.description }}</div>
    </div>
  </div>
</template>

<script>
import parts from '../data/parts';

export default {
  name: 'RobotTorsos',
  data() {
    return { torsos: parts.torsos };
  },
};
</script>
