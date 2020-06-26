<script>
  import { Link } from "svelte-navigator";
  import vars from "../../config/__buildEnv__.json";

  export let to = "";

  function getProps({ location, href, isPartiallyCurrent, isCurrent }) {
    const relativeHref = href.replace(vars.pathPrefix, '');
    const isActive = relativeHref === location ? isCurrent : isPartiallyCurrent || isCurrent;

    console.log('href', href);
    console.log('relativeHref', relativeHref);
    console.log('location', location);
    console.log('isActive', isActive);
    console.log('isCurrent', isCurrent);

    // The object returned here is spread on the anchor element's attributes
    if (isActive) {
      return { class: "active" };
    }
    return {};
  }
</script>

<li class="nav__item">
  <Link {to} {getProps}>
    <slot />
  </Link>
</li>
