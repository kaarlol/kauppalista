<template>
  <v-container fluid>
    <v-flex v-for="(item, i) in items" :key="i">
      <v-card tile class="mb-2">
        <v-card-title>
          <v-row no-gutters>
            <v-col :cols="2" class="d-flex justify-start">
              <v-simple-checkbox
                color="success"
                class="ml-1"
                v-model="items[i].checked"
              ></v-simple-checkbox>
            </v-col>
            <v-col :cols="6" class="d-flex">
              <span class="text-subtitle-1" v-if="!items[i].editing">{{
                item.title
              }}</span>
              <v-text-field
                single-line
                dense
                class="text-subtitle-1"
                v-if="items[i].editing"
                v-model="items[i].title"
                v-on:keyup.enter="saveItem(i)"
              ></v-text-field>
            </v-col>
            <v-col :cols="4" class="d-flex justify-end">
              <v-icon class="mr-1" v-on:click="editItem(i)">mdi-pencil</v-icon>
              <v-icon class="mr-1" v-on:click="items.splice(i, 1)"
                >mdi-close</v-icon
              >
              <v-icon>mdi-drag-horizontal-variant</v-icon>
            </v-col>
          </v-row>
        </v-card-title>
      </v-card>
    </v-flex>
    <v-btn
      fab
      large
      bottom
      fixed
      right
      :style="{ left: '50%', transform: 'translateX(-50%)' }"
      v-on:click="addItem()"
    >
      <v-icon>mdi-plus</v-icon>
    </v-btn>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: [
      { title: "Peruna", editing: false, checked: false },
      { title: "Porkkana", editing: false, checked: false },
      { title: "Possu", editing: false, checked: false },
    ],
  }),
  methods: {
    saveItem: function (index) {
      this.items[index].editing = false;
    },
    editItem: function (index) {
      if (this.items[index].editing === false) {
        this.items[index].editing = true;
      } else {
        this.saveItem(index);
      }
    },
    addItem: function () {
      this.items.push(
          { title: "", editing: true, checked: false }
          );
    },
  },
};
</script>