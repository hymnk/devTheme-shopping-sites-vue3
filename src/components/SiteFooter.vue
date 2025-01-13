<template>
  <footer class="footer">
    <div class="footer-bottom">
      <p>© 2025 Footer Area.</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'SiteFooter'
}
</script>

<style scoped>
.footer {
  background-color: #666;
  position: fixed;
  bottom: 0;
  width: 100%;
}

.footer-bottom {
  text-align: center;
  padding: 1em 0;
  border-top: 3px solid #333;
}

.footer-bottom p {
  color: #eee;
  font-size: 120%;
}
</style>
