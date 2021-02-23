<template>
  <div>
    <b-navbar toggleable="lg"  variant="light">
      <b-container>
        <b-navbar-brand href="#">Store.com</b-navbar-brand>

        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">


            <b-navbar-nav>
              <b-nav-item href="#" >Home</b-nav-item>
              <b-nav-item href="#" >Store</b-nav-item>
              <b-nav-item href="#" >About</b-nav-item>
              <b-nav-item href="#" >Contact</b-nav-item>
            </b-navbar-nav>

          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
  </div>
</template>

<script>
export default {
  name: "NavbarComplejo",
};
</script>

<style lang="scss" scoped></style>
