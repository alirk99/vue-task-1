<template>
  <v-main>
      <v-card 
         class="mx-auto rounded" 
         :elevation="5"
         tile>
         <Task v-for="(task,i) in getTodos" :key="i" :task="task"  />
         <!-- {{getTodos}} -->
      </v-card>
  </v-main>
</template>

<script>
import Task from "../components/Task.vue";
import { mapActions, mapGetters, mapMutations } from "vuex";

export default {
  name: "AllTasks",
  data() {
      return {

      };
   },
   created() {
      this.$emit("loading", true);
      this.fetchTodos();
   },
   updated() {
      this.$emit("loading", false);
      this.findPending();
   },
   computed: {
      ...mapGetters(["getTodos"]),

      },
   methods: {
      ...mapActions(["fetchTodos",]),
      ...mapMutations(["findPending"]),
      
   },
   props: {

   },
   components: {
      Task,
   },
};
</script>

<style scoped>

</style>