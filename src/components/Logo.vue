<template>
  <g-link class="logo" to="/">
    <g-image
      alt="Jared Gomes author of JaredGomes.com"
      class="logo__image"
      src="~/assets/images/jared_gomes.png"
    />
    <span class="logo__text"> {{ $static.metadata.siteName }} </span>
  </g-link>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style lang="scss">
.logo {
  text-decoration: none;
  color: var(--body-color) !important;
  font-size: 0.9em;

  &__image {
    vertical-align: middle;
    height: 40px;
    width: 40px;
    margin-right: 0.5em;
  }
}
</style>
