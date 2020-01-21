<template>
  <div class="author">
    <g-image
      alt="Jared Gomes author of JaredGomes.com"
      class="author__image"
      src="~/assets/images/jared_gomes.png"
      width="180"
      height="180"
      blur="5"
    />

    <h1 v-if="showTitle" class="author__site-title">
      {{ $static.metadata.siteName }}
    </h1>

    <p class="author__intro">
      Just another ordinary web developer documenting their journey through this
      ever-changing space.
    </p>

    <p class="author__links">
      <a
        aria-label="Jared Gomes Youtube Channel"
        href="//www.youtube.com/channel/UCL08qIMArqj2CCCyTyJ21Lg"
        target="_blank"
        rel="noopener"
        ><font-awesome :icon="['fab', 'youtube']"
      /></a>
      <a
        aria-label="Jared Gomes Github Page"
        href="//github.com/Jared-Gomes"
        target="_blank"
        rel="noopener"
        ><font-awesome :icon="['fab', 'github']"
      /></a>
      <a
        aria-label="Jared Gomes Twitter Feed"
        href="//twitter.com/Jared_Gomes_"
        target="_blank"
        rel="noopener"
        ><font-awesome :icon="['fab', 'twitter']"
      /></a>
    </p>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
export default {
  props: ['showTitle']
};
</script>

<style lang="scss">
.author {
  margin: 0 auto;
  max-width: 500px;
  text-align: center;
  padding: calc(var(--space) / 2) 0;

  &__image {
    border-radius: 100%;
    width: 90px;
    height: 90px;
    margin-bottom: 1em;
  }

  &__intro {
    opacity: 0.8;
  }

  &__site-title {
    font-size: 1.5em;
  }

  &__links {
    margin-top: -0.5em;
    a {
      margin: 0 0.5em;
    }
  }
}
</style>
