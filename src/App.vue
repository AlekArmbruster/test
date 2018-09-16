<template>
  <div id="app">
    <nav class="navbar navbar-dark bg-dark">
      <ul class="navbar-nav mr-auto">
            <router-link tag="li" class="nav-item" to="/customers" active-class="active">
              <a class="nav-link">Customers</a>
            </router-link>
            <router-link tag="li" class="nav-item" to="/products" active-class="active">
              <a class="nav-link">Products</a>
            </router-link>
          </ul>
    </nav>
    <div class="container">
      <router-view/>
    </div>
  </div>
</template>
