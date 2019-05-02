<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="primary">
      <b-navbar-brand href="/">My Store</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item href="/about-us">About Us</b-nav-item>
        </b-navbar-nav>

        <b-navbar-nav class="ml-auto">
          <b-nav-item-dropdown text="Products" right>
            <b-dropdown-item
              v-for="product in products"
              :key="product.urlname"
              :href="`/${product.urlname}`"
            >
              {{ product.name }}
            </b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data() {
    return {
      products: []
    }
  },
  apollo: {
    products: gql`
      {
        products: alchemyPages(pageLayout: "product") {
          name
          urlname
        }
      }
    `
  }
}
</script>
