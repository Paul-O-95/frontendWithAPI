<script>
  export let segment;
  let showNav = false;
  if (segment !== ".") {
    showNav = true;
  }
</script>

<style>
  nav {
    border-bottom: 1px solid rgba(255, 62, 0, 0.1);
    font-weight: 300;
    padding: 0 1em;
  }
  ul {
    margin: 0;
    padding: 0;
    text-align: right;
  }
  /* clearfix */
  ul::after {
    content: "";
    display: block;
    clear: both;
  }
  li {
    display: inline-block;
  }
  [aria-current] {
    position: relative;
    display: inline-block;
  }
  [aria-current]::after {
    position: absolute;
    content: "";
    width: calc(100% - 1em);
    height: 2px;
    background-color: rgb(255, 62, 0);
    display: block;
    bottom: -1px;
  }
  a {
    text-decoration: none;
    padding: 1em 0.5em;
    display: block;
  }
</style>

{#if segment}
  <nav>
    <ul>
      <li>
        <a aria-current={segment === 'home' ? 'page' : undefined} href="home">
          compare
        </a>
      </li>
      <li>
        <a
          rel="prefetch"
          aria-current={segment === 'result' ? 'page' : undefined}
          href="result">
          history
        </a>
      </li>

      <!-- for the blog link, we're using rel=prefetch so that Sapper prefetches
		     the blog data when we hover over the link or tap it on a touchscreen -->
      <li>
        <a aria-current={segment === '.' ? 'page' : undefined} href=".">
          logout
        </a>
      </li>
    </ul>
  </nav>
{/if}
