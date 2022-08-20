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
          <p>
            Blackboard Nepal was born with an idea of empowering the community. We beleive that the best way of empowerment is through information. We will be writing on topics such as Technology, Language and Literature, Health and nutrition, Finance and so on
          </p>
          <p>
            You can search for articles using the search bar on the top or go on categories and browse the categories
          </p>
        </div>
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
