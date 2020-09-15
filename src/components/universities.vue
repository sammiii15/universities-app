<template>
  <v-container fluid class="my-img">
    <v-row justify="center" class="mx-0">
      <v-col cols="12" sm="12" md="10" lg="10" v-if="university">
        <v-card>
          <v-card-title>
            <v-text-field
              v-model="search"
              label="Search"
              single-line
              color="black"
              hide-details></v-text-field>
          </v-card-title>

          <v-data-table
             :headers="headers"
             :items="university"
             :items-per-page="20"
             :search="search"
             class="elevation-1"></v-data-table>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import axios from "axios";

  export default {
    name: 'universities',

    data: () => ({
      university: null,
      search: null,
      headers: [
          {
            text: 'Universidades',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'Sitio web', value: 'web_pages' },
          { text: 'Código', value: 'alpha_two_code' },
          { text: 'Estado / Provincia', value: 'state-province' },
          { text: 'Dominios', value: 'domains' },
          { text: 'Pais', value: 'country' },
        ]
    }),
    mounted() {
      this.getUniversities()
    },
    created() {
      this.getUniversities()
    },
    methods: {
    getUniversities: function() {
      axios
        .get('https://raw.githubusercontent.com/Hipo/university-domains-list/master/world_universities_and_domains.json')
        .then(response => (
          this.university = response.data))
        .catch(({ response }) => {
          const { data } = response
            for (const error in data) {
              this[`${error}Error`] = data[error][0]
            }
          })
      }
    }   
  }
</script>
<style scoped lang="scss">
  .my-img {
    background-color:gray;
    background-repeat: repeat;
    background-size: 90%;
  }

</style>
