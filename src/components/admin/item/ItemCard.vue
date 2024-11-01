<!--Raynaldi-->

<!-- Komponen Custom -->
<template>
  <div class="item-card card mb-3" >
    <div class="card-body">
      <h3 class="card-title">{{ item.nama }}</h3>
      <p class="card-text">{{ item.deskripsi }}</p>
      <p class="card-text stock">Stok: {{ item.stok }}</p>
    
      <div class="buttons d-flex gap-2 mt-3">
       <!--<button @click="$emit('edit-item', item)" class="edit">Edit</button>
        <button @click="$emit('delete-item', item.kode)" class="delete">Delete</button>
      -->
      <button @click="$emit('edit-item', item)" 
      class="btn btn-success edit ">Edit</button>
      
      <button @click="$emit('delete-item', item.kode)" 
      class="btn btn-danger delete">Delete</button>
      </div>

     </div> 
  </div>
</template>

<script>
export default {
  name: "ItemCard",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
};
</script>


<style scoped>
.item-card  {
  transition: transform 0.2s, box-shadow 0.2s;
  /*
    border: 1px solid #ddd;
    padding: 16px;
    margin-bottom: 10px;
    border-radius: 8px;
    background-color: #f9f9f9;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);

    */
}

.item-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.item-card.title {
  margin: 0 0 10px;
  font-size: 1.5rem;
  color: #333;
}

.item-card .card-text {
  margin: 5px 0;
  color: #555;
}

/*
.item-card h3 {
    margin: 0 0 10px;
    font-size: 1.5em;
    color: #333;
}
.item-card p {
    margin: 5px 0;
    color: #555;
}
.item-card .stock {
    font-weight: bold;
    color: #2c3e50;
}
.item-card .buttons {
    display: flex;
    gap: 10px;
    margin-top: 10px;
}
.item-card button {
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.2s;
}
.item-card button:hover {
    background-color: #ddd;
}
.item-card button.edit {
    background-color: #4caf50;
    color: white;
}
.item-card button.edit:hover {
    background-color: #45a049;
}
.item-card button.delete {
    background-color: #e74c3c;
    color: white;
}
.item-card button.delete:hover {
    background-color: #c0392b;
}

*/
</style>