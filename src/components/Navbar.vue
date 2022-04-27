<template>
  <nav id="nav">
   <router-link to="/" id="logo_url">
     <img :src="logo" :alt="alt" id="logo">
   </router-link>
    <router-link to="/">Home</router-link> 
    <router-link to="/Pedidos">About</router-link>
  </nav>
</template>
<script>
export default {
 name:'Navbar',
 props:["logo", "alt"]
}
</script>
<style scoped>
 #nav {
  background:#222;
  border-bottom:  4px solid #111;
  
  padding: 15px 50px;

  display: flex;
  align-items: center;
  justify-content: flex-end;
  
 }

 #nav #logo_url {
  margin:auto;
  margin-left: 0;
 }

#logo {
 width: 40px;
 height: 40px;
}

#nav a {
 color: #fcba03;
 text-decoration: 0;
 font-weight: 600;
 font-size: 18px;
 line-height: 24px;

 margin: 12px;
 transition: .5s;
}

#nav a:hover {
 color: white;
}
</style>
