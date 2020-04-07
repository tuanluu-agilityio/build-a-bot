<template>
  <div class="content">
    <button class="add-to-cart" @click="addToCart()">Add to Cart</button>
    <div class="top-row">
        <!-- <div class="robot-name">
          {{selectedRobot.head.title}}
          <span v-if="selectedRobot.head.onSale" class="sale">Sale!</span>
        </div> -->
      <PartSelector :parts="availableParts.heads" />
    </div>
    <div class="middle-row">
      <PartSelector :parts="availableParts.arms" />
      <PartSelector :parts="availableParts.torsos" />
      <PartSelector :parts="availableParts.arms" />
    </div>
    <div class="bottom-row">
      <PartSelector :parts="availableParts.bases" />
    </div>
    <div>
      <table>
        <thead>
          <tr>
            <th>Robot</th>
            <th class="cost">Cost</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(robot, index) in cart" :key="index">
            <td>{{robot.head.title}}</td>
            <td class="cost">{{robot.cost}}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import availableParts from '../data/parts';
import createdHookMixin from './created-hook-mixin';
import PartSelector from './PartSelector.vue';

export default {
  name: 'RobotBuilder',
  components: { PartSelector },
  data() {
    return {
      availableParts,
      cart: [],
      selectedRobot: {
        head: {},
        leftArm: {},
        torso: {},
        rightArm: {},
        base: {},
      },
    };
  },
  mixins: [createdHookMixin],
  computed: {
    saleBorderClass() {
      return this.selectedRobot.head.onSale ? 'sale-border' : '';
    },
    headBorderStyle() {
      return {
        border: this.selectedRobot.head.onSale ? '3px solid red' : '3px solid #aaa',
      };
    },
  },
  methods: {
    addToCart() {
      const robot = this.selectedRobot;
      const cost = robot.head.cost
        + robot.leftArm.cost
        + robot.torso.cost
        + robot.rightArm.cost
        + robot.base.cost;
      this.cart.push({ ...robot, cost });
    },
  },
};
</script>

<style lang="scss" scoped>
.content {
  position: relative;
}
.add-to-cart {
  position: absolute;
  right: 30px;
  width: 220px;
  padding: 3px;
  font-size: 16px;
}
td, th {
  text-align: left;
  padding: 5px;
  padding-right: 20px;
}
.cost {
  text-align: right;
}
.sale-border {
  border: 3px solid red;
}
</style>
