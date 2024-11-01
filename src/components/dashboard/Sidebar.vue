<!-- Raynaldi -->

<template>
  <div :class="['sidebar', { 'd-none': !isSidebarVisible }]">
    <a class="logo dblock text-center mb-4 text-white" >Simbok</a>
    <ul class="nav flex-column">
      <li v-if="currentRole === 'admin'" class="nav-item">
        <a href="#" @click.prevent="showComponent('users')" 
        class="nav-link text-white d-flex">
          <i class="bi bi-house-door me-2"></i> Users
        </a>
      </li>
      <li class="nav-item">
        <a href="#" @click.prevent="showComponent('items')" 
        class="nav-link text-white d-flex">
          <i class="bi bi-box me-2"></i> Items
        </a>
      </li>
      
      <li class="nav-item">
        <a href="#" @click.prevent="showComponent('transactions')" class="nav-link text-white d-flex">
          <i class="bi bi-cash me-2"></i> Transactions
        </a>
      </li>

      <li v-if="currentRole == 'user'" class="nav-item">
        <a href="#" @click.prevent="showComponent('history')" class="nav-link text-white d-flex">
          <i class="bi bi-clock-history me-2"></i> History
        </a>
      </li>
    </ul>
  </div>
</template>  

<script>
export default {
  props: {
      currentRole: {
          type: String,
          required: true,
      },
      isSidebarVisible: {
          type: Boolean,
          required: true,
      },
  },
  methods: {
      showComponent(component) {
          this.$emit("showComponent", component);
      },
  },
  emits: ["showComponent"],
};
</script>

<style scoped>
.sidebar {
width: 200px;
background: #4b3f6b;
color: white;
padding: 14px;
height: 100vh;
position: fixed;
top: 0;
left: 0;
z-index: 999;
font-size: 18px;
font-family: sans-serif;
transition: transform 0.3s ease = ease-in-out;
transform: translateX(-2);
}
.sidebar .d-none {
display: none;
transform: translateX(-200px);
}

.sidebar.hidden {
  transform: translateX(-100%);
}

.logo {
  /*font-size: 24px;
  margin-bottom: 30px;
  font-weight: bold;
  text-align: center;
  color: white;*/

  font-size: 24px;
  margin: 0 auto 30px;
  font-weight: bold;
  text-align: center;
  color: white;
  display: block;

}
ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 0px;
  text-align: center;
}

nav-link {
  color: white;
  /*text-decoration: none;*/
  cursor: pointer;
  /*display: flex;
  align-items: center;
  justify-content: center;
  padding: 10px 0; */
  transition: background color 0.3s ease;
}
.nav-link:hover {
  text-decoration: underline;
  background-color: rgba(255, 255, 255, 0.1);
}
</style>