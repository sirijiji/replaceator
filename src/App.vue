<template>
  <div id="app" class="layout1">

    <header id="pageHeader">Replaceator</header>
    <article id="mainArticle">

      center


      <div class="field">
          <input class="input is-large" type="text" placeholder="Large input">
      </div>
      <div class="field">
        <button type="submit">Generate</button>
      </div>

    </article>
    <result id="result"> result</result>
    <nav id="mainNav">Nav

      <div class="field">
          <input class="input is-large" type="text" placeholder="Large input">
      </div>

    </nav>

    <footer id="pageFooter">Footer</footer>

  </div>
</template>

<script>


export default {
  name: 'App',
  components: {

  }
}
</script>

<style>

  .layout1 {
    display: grid;
    grid-template-areas:
    "header header header"
    "nav article article"
    "nav result result"
    "footer footer footer";
    grid-template-rows: 60px 1fr 60px;
    grid-template-columns: 20% 1fr 15%;
    grid-gap: 10px;
    height: 100vh;
    margin: 0;
  }
  header, footer, article, result, nav, div {
    padding: 10px;
    background: white;
    border-style: solid;
  }
  #pageHeader {
    grid-area: header;
  }
  #pageFooter {
    grid-area: footer;
  }
  #mainArticle {
    grid-area: article;
  }
  #result {
    grid-area: result;
  }
  #mainNav {
    grid-area: nav;
  }
  #siteAds {
    grid-area: ads;
  }
</style>
