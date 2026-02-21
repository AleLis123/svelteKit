<script lang="ts">
</script>

<header class="site-header">
  <div class="inner">
    <div class="logo">
      Arktyczna Przygoda
    </div>

    <nav class="nav">
      <a href="/">Start</a>
      <a href="/wyprawy">Wyprawy</a>
      <a href="/o-nas">O nas</a>
      <a href="/kontakt">Kontakt</a>
    </nav>
  </div>
</header>

<style>
  .site-header {
    width: 100%;
    height: 90px; /* jak w Twoim divie */
    background-color: #f5f5f5; /* identyczny kolor */
    position: fixed; /* globalnie na górze */
    top: 0;
    left: 0;
    z-index: 1000;
    border-radius: 0; /* brak zaokrągleń */
    box-shadow: none;
  }

  .inner {
    max-width: 1200px;
    height: 100%;
    margin: 0 auto;
    padding: 0 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .logo {
    font-size: 1.4rem;
    font-weight: 600;
    color: #111;
  }

  .nav a {
    margin-left: 32px;
    text-decoration: none;
    color: #111;
    font-weight: 500;
    transition: opacity 0.2s ease;
  }

  .nav a:hover {
    opacity: 0.6;
  }
</style>