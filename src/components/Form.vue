<template>
  <div>
    <h2>Form Data Skincare</h2>
    <form @submit.prevent="submitForm" class="expense-form">
      <div class="form-group">
        <label for="description">Nama Skincare</label>
        <input type="text" v-model="description" class="form-control" placeholder="Masukkan nama Skincare">
      </div>
      <div class="form-group">
        <label for="price">Harga Skincare</label>
        <input type="number" v-model.number="price" class="form-control" placeholder="Masukkan harga Skincare">
      </div>
      <div class="form-group">
        <label for="quantity">Jumlah Skincare</label>
        <input type="number" v-model.number="quantity" class="form-control" placeholder="Masukkan jumlah Skincare">
      </div>
      <button type="submit" class="btn">Tambahkan</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'ExpenseForm',
  data() {
    return {
      description: '',
      price: '',
      quantity: ''
    };
  },
  methods: {
    submitForm() {
      const total = this.price * this.quantity;
      const expense = {
        description: this.description,
        price: this.price,
        quantity: this.quantity,
        total: total
      };
      this.$emit('add-expense', expense);
      this.clearForm();
    },
    clearForm() {
      this.description = '';
      this.price = 0;
      this.quantity = 1;
    }
  }
}
</script>

<style scoped>
.expense-form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.form-group {
  display: flex;
  flex-direction: column;
}

label {
  margin-bottom: 5px;
}

.form-control {
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 3px;
}

.btn {
  background-color: #3498db;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}

.btn:hover {
  background-color: #2980b9;
}
</style>
