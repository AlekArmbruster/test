<template>
  <div>
    <h1>Products</h1>
    <hr/>

    <input type="text" class="form-control mb-3" placeholder="Search" v-model="searchTerm" style="width: 18rem;">
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Name</th>
          <th scope="col">Quantity</th>
          <th scope="col">&nbsp;</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id" v-if="product.name.toLowerCase().includes(searchTerm.toLowerCase())">
          <td>{{ product.name }}</td>
          <td>{{ product.quantity }}</td>
          <td class="text-right">
            <router-link class="btn btn-light btn-sm mr-2" :to="{ name: 'purchase-product', params: { id: product.id }}">
              <i class="fas fa-shopping-cart"></i>
            </router-link>
            <button class="btn btn-light btn-sm mr-2" @click="increment(product)">+</button>
            <button class="btn btn-light btn-sm" @click="decrement(product)">-</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  import { productService } from '../utils/ProductService'

  export default {
    data() {
      return {
        products: productService.list(),
        searchTerm: ''
      }
    },

    methods: {
      increment(product) {
        productService.increment(product)
      },

      decrement(product) {
        productService.decrement(product)
      }
    }
  }
</script>
