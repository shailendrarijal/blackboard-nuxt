<template>
  <div id="about-page" class="page-wrapper about-page content-page">
    <site-hero
      title=""
      subtitle=""
      image="/uploads/about-logo.png"
    ></site-hero>
    <main-section theme="sidebar-right">
      <template v-slot:default>
        <div class="content">
          <h3>About Blackboard Nepal</h3>
          /*<p>
            <strong>
              Edit this page in<code>/pages/about.vue</code>to fit your needs.
            </strong>
          </p>*/
          <p>
            Blackboard Nepal was born with an idea of empowering the community. We beleive that the best way of empowerment is through information. We will be writing on topics such as Technology, Language and Literature, Health and nutrition, Finance and so on
          </p>
          <p>
            You can search for articles using the search bar on the top or go on categories and browse the categories
          </p>
        </div>

        /*<div class="tile is-ancestor">
          <div class="tile is-parent">
            <article class="tile is-child box">
              <p class="title">
                Cool Stuff We Do
              </p>
              <p class="subtitle">
                Sooo Cool
              </p>
              <figure class="image is-1by1">
                <opti-image width="500" height="500" />
              </figure>
            </article>
          </div>
          <div class="tile is-parent">
            <article class="tile is-child box">
              <p class="title">
                Other Cool Things
              </p>
              <p class="subtitle">
                Just as cool
              </p>
              <figure class="image is-1by1">
                <opti-image width="500" height="500" />
              </figure>
            </article>
          </div>
          <div class="tile is-parent">
            <article class="tile is-child box">
              <p class="title">
                All the cool
              </p>
              <p class="subtitle">
                that is all
              </p>
              <figure class="image is-1by1">
                <opti-image width="500" height="500" />
              </figure>
            </article>
          </div>
        </div>*/
      </template>

      <template v-slot:sidebar>
        <h3 class="subtitle is-4">
          Latest Posts
        </h3>
        <posts-grid :per-row="1" :number="2" />
      </template>
    </main-section>
  </div>
</template>
<script>
import QuoteCard from '~/components/cards/QuoteCard'
export default {
  head() {
    return {
      title: `About | ${this.$siteConfig.siteName}`
    }
  },
  components: { QuoteCard }
}
</script>
