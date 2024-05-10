<template>
  <div class="container">
    <h2 class="title">Tambah Kontak WhatsApp</h2>
    <form @submit.prevent="addContact" class="form">
      <div class="form-group">
        <label for="name">Nama:</label>
        <input type="text" id="name" v-model="name" class="form-control" required>
      </div>
      <div class="form-group">
        <label for="number">Nomor WhatsApp:</label>
        <input type="text" id="number" v-model="number" class="form-control" required>
      </div>
      <button type="submit" class="btn btn-primary">Tambah Kontak</button>
    </form>

    <h2 class="title">Daftar Kontak WhatsApp</h2>
    <ul>
      <li v-for="(contact, index) in contacts" :key="index" class="contact-item">
        <div>{{ contact.name }} - {{ contact.number }}</div>
        <button @click="deleteContact(index)" class="btn btn-delete">Hapus</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contacts: [
      ],
      name: '',
      number: ''
    }
  },
  methods: {
    addContact() {
      if (this.name && this.number) {
        this.contacts.push({ name: this.name, number: this.number });
        this.name = '';
        this.number = '';
      } else {
        alert('Nama dan Nomor WhatsApp harus diisi!');
      }
    },
    deleteContact(index) {
      this.contacts.splice(index, 1);
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.title {
  color: #333;
}

.form-group {
  margin-bottom: 20px;
}

.form-control {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.btn {
  padding: 10px 20px;
  font-size: 16px;
  border-radius: 5px;
  cursor: pointer;
}

.btn-primary {
  background-color: #007bff;
  color: #fff;
  border: none;
  transition: background-color 0.3s;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.btn-delete {
  background-color: #dc3545;
  color: #fff;
  border: none;
  transition: background-color 0.3s;
}

.btn-delete:hover {
  background-color: #c82333;
}

.contact-item {
  margin-top: 10px;
}
</style>
