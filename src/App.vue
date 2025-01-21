<template>
  <div>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <span>{{ item.label }}</span>
        <button @click="navigateToPage(item.id)">Select</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [{label:'Rais'}, {label:'Sana'}], // List of items from the API
    };
  },
  mounted() {
    this.fetchItems();
  },
  methods: {
    // Fetch data from your API
    async fetchItems() {
      try {
        const response = await fetch('https://api.example.com/items'); // Replace with your API
        const data = await response.json();
        //this.items = data; // Populate items with the API response
      } catch (error) {
        console.error('Error fetching items:', error);
      }
    },

    // Navigate to another page on button click
    navigateToPage(id) {
      this.$router.push({ name: 'item-details', params: { id } }); // Assuming 'item-details' is a route
    },
  },
};
</script>