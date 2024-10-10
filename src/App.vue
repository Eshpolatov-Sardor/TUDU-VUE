<template>
  <div class="container">
    <div class="tudu-now">
      <WelcomeItem />
    </div>
  </div>
</template>
<script>
import WelcomeItem from "./components/WelcomeItem.vue";
export default {
  components: { WelcomeItem },
  props: {
    count: {
      type: Number,
      required: true
    }
  },
  data() {
    return {

    }
  },
};
</script>
<style></style>
