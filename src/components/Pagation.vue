<template>
  <div class="page-nav-container">
    <div v-if="last >= 5" class="page-nav">
      <div v-bind:class="(current == 1) ?      'page-button selected-page-button':'page-button'"
        @click="updatePager(1)">1«</div>
      <div v-bind:class="(current == b2) ? 'page-button selected-page-button':'page-button'"
        @click="updatePager(b2)">{{b2}}</div>
      <div v-bind:class="(current == b3) ? 'page-button selected-page-button':'page-button'"
        @click="updatePager(b3)">{{b3}}</div>
      <div v-bind:class="(current == b4) ? 'page-button selected-page-button':'page-button'"
        @click="updatePager(b4)">{{b4}}</div>
      <div v-bind:class="(current == last) ? 'page-button selected-page-button':'page-button'"
        @click="updatePager(last)">»{{last}}</div>
    </div>

    <div v-if="last < 5" class="page-nav">
      <div v-for="index in parseInt(last)" :key="index"
        v-bind:class="(current == index) ? 'page-button selected-page-button':'page-button'" @click="updatePager(index)">
        {{ index }} 
      </div>
    </div>
  </div>
</template>

<style scoped>
.page-nav {
        display: flex;
    }

    .page-nav-container {
        margin-left: auto;
        margin-right: auto;
    }
    .page-button {
      text-align: center;
        padding: 10px;
        width: 50px;
        height: 50px;
        -webkit-user-select: none; /* Safari */
        -ms-user-select: none; /* IE 10 and IE 11 */
        user-select: none; /* Standard syntax */
    }
    .selected-page-button {
        background-color: #5676f4;
        border-radius: 50%;
    }
    .unclaimed-loading {
        padding-top: 20vh;
        padding-bottom: 30vh;
    }
</style>


<script>
export default {
  props: {
    current: Number,
    last: Number
  },
  methods: {
    updatePager: function (newCurrent) {
      if (this.current == newCurrent) {
        return
      }
      this.$emit("updatePager", newCurrent);
    },
  },
  computed: {

    b2() {
      if (this.current <= 3) {
        return 2
      }
      else if (this.last - this.current < 3) {
        return this.last - 3
      }
      else {
        return this.current - 1

      }
    },
    b3() {
      if (this.current <= 3) {
        return 3
      }
      else if (this.last - this.current < 3) {
        return this.last - 2
      }
      else {
        return this.current
      }
    },
    b4() {
      if (this.current <= 3) {
        return 4
      }
      else if (this.last - this.current < 3) {
        return this.last - 1
      }
      else {
        return this.current + 1

      }
    },
  }
};
</script>