<template>
  <div id="footer">
    <p>Make Your Burger &copy; 2022</p>
  </div>
</template>
<script>
export default {
  name: "Footer",
};
</script>
<style scoped>
#footer {
  background-color: #222;
  width: 100%;
  height: 200px;
  border-top: 4px solid #111;

  display: flex;
  align-items: center;
  justify-content: center;
}
#footer p {
  color: #fcba03;
  text-decoration: 0;
  font-weight: 600;
  font-size: 18px;
  line-height: 24px;
}
</style>
