<!--Raynaldi-->

<template>
  <div class="item-list container py-4">
    <div class="header d-flex justify-content-between align-items-center mb-3">
      <h2>Daftar Barang</h2>
      <button class="btn btn-primary" @click="showAddForm">Tambah Item</button>
      <!--<button class="add-btn" @click="showAddForm">Tambah Item</button>-->
      <!--<button class="add-btn" @click="$emit('add-item')">Tambah Item</button> -->
    </div>

    <div class="item-cards row">
      <ItemCard v-for="item in items" :key="item.kode" :item="item" @edit-item="editItem" @delete-item="deleteItem" 
      class="col-md-6 col-lg-6"/>
    </div>

    <!-- Diganti menggunakan item-cards -->
    <!-- <div class="table-responsive">
        <table>
          <thead>
            <tr>
              <th>Kode Barang</th>
              <th>Nama Barang</th>
              <th>Deskripsi</th>
              <th>Stok</th>
              <th class="action-column">Aksi</th>
            </tr>
          </thead>
  
          <tbody>
            <tr v-for="item in items" :key="item.kode">
              <td>{{ item.kode }}</td>
              <td>{{ item.nama }}</td>
              <td>{{ item.deskripsi }}</td>
              <td>{{ item.stok }}</td>
              <td class="action-column action-buttons">
                <button class="edit-btn" @click="$emit('edit-item', item)">Edit</button>
                <button class="delete-btn" @click="deleteItem(item.kode)">Delete</button>
              </td>
            </tr>
          </tbody>
        </table>
      </div> -->

    <Modal :visible="showForm" @close="cancelEditForm">
      <ItemForm :item="selectedItem" :isEdit="isEdit" @submit="handleSubmit" 
      @cancel="cancelEditForm" />
    </Modal>
    
  </div>
  <!-- end div of item-list -->
</template>

<script>
//Import Komponen Custom
import ItemCard from "./ItemCard.vue";
import Modal from "../../Modal.vue";
import ItemForm from "./ItemForm.vue";

export default {
  //export komponen custom
  components: {
    ItemCard,
    Modal,
    ItemForm,
  },

  data() {
    return {
      items: [
        {
          kode: "2024001",
          nama: "Acer Nitro 15 AN515-58",
          deskripsi: "Intel Core i5 12500H, RTX 3050, RAM 8GB DDR4, LAYAR 15.6",
          stok: 80,
        },
        {
          kode: "2024002",
          nama: "Lenovo LOQ 15 15IRH8",
          deskripsi: "Intel Core i5 13450H, RTX 3050, RAM 8GB DDR4, LAYAR 15.6",
          stok: 80,
        },
      ],
      showForm: false,
      selectedItem: null,
      isEdit: false,
    };
  },

  methods: {
    showAddForm() { //text lms (beda dikit)
      this.selectedItem = { kode: "", nama: "", deskripsi: "", stok: 0 };
      this.isEdit = false;
      this.showForm = true;
    },

    editItem(item) { // lms text dan video
      this.selectedItem = { ...item };
      this.isEdit = true;
      this.showForm = true;
    },


    handleSubmit(item) { //text lms
      if (
        item.kode &&
        item.nama &&
        item.deskripsi &&
        item.stok !== null &&
        !isNaN(item.stok)
      ) {
        if (this.isEdit) {
          const index = this.items.findIndex((i) => i.kode === item.kode);

          this.items[index] = item;
        } else {
          this.items.push(item);
        }
      }

      this.showForm = false;
    },

    cancelEditForm() {
      this.showForm = false;
      this.selectedItem = null; //text lms rev =
      this.isEdit = false; //text lms rev =
    },

    deleteItem(kode) {
      this.items = this.items.filter((item) => item.kode !== kode);
      this.$emit("delete-item", kode); //video lms
    },
  },
}; // end of export default
</script>


<style scoped>
.item-list {
  padding: 24px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin: 20px 0;
  /*margin: auto;*/
}

.header h2 {
    color: #4b3f6b;
    font-size: 24px;
}
.header .btn-primary {
    background-color: #007bff;
    border-color: #007bff;
}
.header .btn-primary:hover {
    background-color: #0056b3;
    border-color: #0056b3;
}

</style>
