<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="actions">
      <h3 @click="toggleHide()">{{ project.title }}</h3>
      <div class="icon">
        <router-link :to="{ name: 'EditProject', params: { id: project.id } }">
          <!-- <span class="material-icons"> edit </span> -->
          <span> edit </span>
        </router-link>
        <!-- <span class="material-icons" @click="deleteProject"> delete </span> -->
        <span @click="deleteProject"> delete </span>
        <!-- <span class="material-icons tick" @click="toggleComplete"> done </span> -->
        <span @click="toggleComplete"> finish </span>
      </div>
    </div>
    <div v-if="showDetails">
      <p class="details">{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
import { thisExpression } from "@babel/types";

export default {
  props: ["project"],
  data() {
    return {
      showDetails: false,
      url: "http://localhost:3000/projects/" + this.project.id,
    };
  },

  methods: {
    // show and hide details
    toggleHide() {
      this.showDetails = !this.showDetails;
    },
    deleteProject() {
      fetch(this.url, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id))
        .catch((err) => console.log(err.message));
    },
    toggleComplete() {
      fetch(this.url, {
        method: "PATCH",
        headers: { "Content-type": "application/json" },
        body: JSON.stringify({ complete: !this.project.complete }),
      })
        .then(() => this.$emit("complete", this.project.id))
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style scoped>
.project {
  margin: 20px auto;
  background: white;
  padding: 10px 20px;
  border-radius: 4px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.05);
  border-left: 4px solid blue;
}
h3 {
  cursor: pointer;
}
.actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.material-icons {
  font-size: 24px;
  margin-left: 10px;
  color: #bbb;
  cursor: pointer;
}
.material-icons:hover {
  color: #777;
}

/* completed projects */
.project.complete {
  /* border-left: 4px solid #0160aa; */
  border-left: 4px solid #00ce90;
}

.project.complete .tick {
  color: #00ce89;
}
</style>
