<template>
  <form @submit.prevent="calculatePixel">
    <div class="flex flex-col justify-around items-center gap-4">
      <div class="flex flex-col items-start justify-center gap-2">
        <span>Starting Position</span>
        <div class="flex gap-4">
          <div class="flex gap-2 items-center">
            <label for="x-one">X-Co-ordinate: </label>
            <input
              type="number"
              name="x-one"
              v-model="firstX"
              class="border-2 rounded-full border-orange-400 focus:border-orange-200 px-4 py-1"
            />
          </div>
          <div class="flex gap-2 items-center">
            <label for="y-one">Y-Co-ordinate: </label>
            <input
              class="border-2 rounded-full border-orange-400 focus:border-orange-200 px-4 py-1"
              type="number"
              v-model="firstY"
              name="y-one"
            />
          </div>
        </div>
      </div>

      <div class="flex flex-col items-start justify-center gap-2">
        <span>Ending Position</span>
        <div class="flex gap-4">
          <div class="flex gap-2 items-center">
            <label for="x-two">X-Co-ordinate: </label>
            <input
              type="number"
              name="x-two"
              v-model="secondX"
              class="border-2 rounded-full border-orange-400 focus:border-orange-200 px-4 py-1"
            />
          </div>
          <div class="flex gap-2 items-center">
            <label for="y-two">Y-Co-ordinate: </label>
            <input
              class="border-2 rounded-full border-orange-400 focus:border-orange-200 px-4 py-1"
              type="number"
              v-model="secondY"
              name="y-two"
            />
          </div>
        </div>
      </div>
      <button
        class="bg-orange-400 px-8 py-2 text-white rounded-full hover:bg-orange-600"
        >Convert</button
      >
    </div>
  </form>

  <div class="flex items-center justify-center my-4">
    <div>
      <div class="flex" v-if="!rasterHidden" v-for="i in maxY">
        <div v-for="j in maxX">
          <div
            class="w-8 h-8 border border-orange-600"
            :class="rows[i][j] ? 'bg-orange-600' : ''"
          ></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      firstX: 0,
      firstY: 0,
      secondX: 0,
      secondY: 0,
      maxX: 0,
      maxY: 0,
      difX: 0,
      difY: 0,
      steps: 0,
      yInc: 0,
      xInc: 0,
      rows: [],
      rasterHidden: true,
      bgColor: "bg-black",
    };
  },
  props: ["stepsTaken", "xIncrement", "yIncrement"],
  methods: {
    calculatePixel() {
      this.rows = [];
      this.difX = this.secondX - this.firstX;
      this.difY = this.secondY - this.firstY;
      this.steps = Math.max(Math.abs(this.difX), Math.abs(this.difY));
      this.maxX = Math.max(this.firstX, this.secondX);
      this.maxY = Math.max(this.firstY, this.secondY);

      this.xInc = this.difX / this.steps;
      this.yInc = this.difY / this.steps;

      for (let i = 0; i <= this.maxY; i++) {
        let row = [];
        for (let j = 0; j <= this.maxX; j++) {
          row.push(false);
        }
        this.rows.push(row);
      }
      // console.log(
      //   this.rows,
      //   "original array",
      //   this.steps,
      //   this.xInc,
      //   this.yInc
      // );

      let x = this.firstX;
      let y = this.firstY;
      for (let i = 0; i <= this.steps; i++) {
        let xRounded = Math.round(x);
        let yRounded = Math.round(y);

        // console.log(x, y, "the increments no round");
        x = x + this.xInc;
        y = y + this.yInc;
        // console.log(xRounded, yRounded, "the increments");

        this.rows[yRounded][xRounded] = true;
      }

      // console.log(this.rows, "its here");
      this.rasterHidden = false;
    },
  },
};
</script>
<style></style>
