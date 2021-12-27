<template>
  <v-container class="mt-10 col-4">
    <v-select v-model="selectedFruits" :items="fruits" clearable attach outlined multiple class="custom-multiselect" :menu-props="{ bottom: true, offsetY: true }">
      <template v-slot:prepend-item>
        <v-list-item>
          <v-list-item-content>
            <v-text-field v-model="searchTerm" placeholder="Поиск" @input="searchFruits"></v-text-field>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-select>
  </v-container>
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
