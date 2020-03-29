<template>
  <div class="navbar">
    <ul class="nav">
      <a href="#about">
        <li class="nav-item">ABOUT</li>
      </a>

      <a href="#projects">
        <li class="nav-item">STUFF</li>
      </a>
      <a href>
        <li class="nav-item">CV</li>
      </a>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style>
.navbar {
  background-color: rgba(250, 250, 250, 0.3);
  font-size: 1.2rem;
  font-weight: 500;
  position: sticky;
  top: 0;
  padding: 2px;
  font-family: "Overpass", sans-serif;
  z-index: 2;
  display: flex;
  flex-direction: row-reverse;
}
.nav {
  list-style-type: none;
  overflow: hidden;
  padding: 5px;
}
.nav-item {
  float: right;
  padding: 8px;
  padding-top: 12px;
}

a {
  color: black;
  text-transform: uppercase;
  text-decoration: none;
  letter-spacing: 0.15em;

  display: inline-block;
  padding: 2px 10px;
  position: relative;
}
a:after {
  background: none repeat scroll 0 0 transparent;
  bottom: 0;
  content: "";
  display: block;
  height: 2px;
  left: 50%;
  position: absolute;
  background: #424242;
  transition: width 0.3s ease 0s, left 0.3s ease 0s;
  width: 0;
}
a:hover:after {
  width: 100%;
  left: 0;
  size: 100% 88%;
}
</style>