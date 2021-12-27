<template>
  <v-select v-model="selectedFruits" :items="fruits" clearable attach dense outlined multiple class="custom-multiselect" :menu-props="{ bottom: true, offsetY: true }" append-icon="mdi-chevron-down">
    <template v-slot:prepend-item>
      <v-list-item class="custom-search-list-item">
        <v-list-item-content>
          <v-text-field v-model="searchTerm" placeholder="Поиск" @input="searchFruits"></v-text-field>
        </v-list-item-content>
      </v-list-item>
    </template>
  </v-select>
</template>

<script>
export default {
  data: () => ({
    searchTerm: "",
    fruits: [
      "Apples",
      "Apricots",
      "Avocado",
      "Bananas",
      "Blueberries",
      "Blackberries",
      "Boysenberries",
      "Bread fruit",
      "Watermelons",
      "Zucchini"
    ],
    fruitsCopy: [],
    selectedFruits: []
  }),
  mounted() {
    this.fruitsCopy = [...this.fruits];
  },
  computed: {},

  methods: {
    searchFruits() {
      if (!this.searchTerm) {
        this.fruits = this.fruitsCopy;
      }

      this.fruits = this.fruitsCopy.filter((fruit) => {
        return fruit.toLowerCase().indexOf(this.searchTerm.toLowerCase()) > -1;
      });
    }
  }
}
</script>
