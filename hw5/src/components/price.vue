<template>
  <div>
    <form @submit.prevent="handleFormSubmit">
      <label for="name">Name</label>
      <input type="text" id="name" v-model="formData.name">
      <label for="date">Date</label>
      <input type="date" id="date" v-model="formData.date" />
      <label for="price">Price</label>
      <input type="number" step ="0.01" id="price" v-model="formData.price" />

      <button type="submit">Submit</button>
    </form>
  </div>

  <div>
    <table>
      <thead>
      <tr>
        <th>name</th>
        <th>date</th>
        <th>price</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(item, index) in data" :key="index">
        <td>{{ item.name }}</td>
        <td>{{ item.date }}</td>
        <td>{{ item.price }}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      data: [],
      formData: {
        name: "",
        date: "",
        price: ""
      }
    };
  },
  methods: {
    handleFormSubmit() {
      this.data.push({
        name: this.formData.name,
        date: this.formData.date,
        price: this.formData.price
      });
      this.formData.name = "";
      this.formData.date = "";
      this.formData.price = "";
    }
  }
};
</script>


<style scoped>

</style>