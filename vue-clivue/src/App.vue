<template>
  <div id="app">
    <div class="content">
      <AppHeader />
      <h2>{{ text }}</h2>
      <Container>
        <ApartmentsFilterForm class="apartments-filter" @submit="filter" />
      </Container>
      <Container>
        <p v-if="!filteredApartments.length">Not found</p>
        <ApartmentsList v-else :items="filteredApartments">
          <template v-slot:apartment="{ apartment }">
            <ApartmentsItem :key="apartment.id" :descr="apartment.descr" :rating="apartment.rating"
              :imgSrc="apartment.imgUrl" :price="apartment.price" @click.native="handleItemClick" />
          </template>
        </ApartmentsList>
      </Container>
    </div>
    <AppFooter />
  </div>
</template>

<script>
import ApartmentsList from './components/Apartments/ApartmentsList'
import ApartmentsItem from './components/Apartments/ApartmentsItem'
import apartments from './components/Apartments/apartments'
import ApartmentsFilterForm from './components/Apartments/ApartmentsFilterForm'
import Container from './components/shared/PageContainer'
import AppFooter from './components/AppFooter'
import AppHeader from './components/AppHeader'

export default {
  name: 'App',
  components: {
    ApartmentsList,
    ApartmentsItem,
    ApartmentsFilterForm,
    Container,
    AppFooter,
    AppHeader,
  },
  data() {
    return {
      text: '',
      apartments,
      filters: {
        city: '',
        price: 0,
      },
    }
  },
  computed: {
    filteredApartments() {
      return this.filterByCityName(this.filterByPrice(this.apartments))
    },
  },
  methods: {
    filter({ city, price }) {
      this.filters.city = city
      this.filters.price = price
    },
    filterByCityName(apartments) {
      if (!this.filters.city) return apartments

      return apartments.filter((apartment) => {
        return apartment.location.city === this.filters.city
      })
    },
    filterByPrice(apartments) {
      if (!this.filters.price) return apartments

      return apartments.filter((apartment) => {
        return apartment.price >= this.filters.price
      })
    },
  },
}
</script>

<style lang="scss" scoped>
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  font-family: Montserrat, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.content {
  flex-grow: 1;
  padding-top: 120px;
}

.apartments-filter {
  margin-bottom: 40px;
}
</style>