<template>
  <main class="post content-box">
    <article
      class="post-60749 page type-page status-publish entry featured-left"
      itemscope
      itemtype="https://schema.org/CreativeWork"
    >
      <header class="entry-header">
        <h1 class="entry-title text-center" itemprop="headline">
          <strong class="type--raleway d-block">Learn how to climb around the 🌍</strong>
          without 🔥 through your 💵 !
        </h1>
      </header>
      <div class="post__content" itemprop="text">
        <article class="mt-3">
          <mailchimp-form :animated="false" />
        </article>
        <div class="section no-line">
          <p class="intro">
            How many times have you saved all your cash for an epic overseas holiday, 
            had an AMAZING time, only to come home broke and bummed out without any 
            idea how you're going to do it again?
          </p>
          <p>
            For years I thought that was just how life was going to be: 
            work, save, travel ... work, save, travel ... 😕 ... And then what!? 
          </p>

          <p>
            <strong><em>This style of travel isn't sustainable</em></strong>. 
            Working dead-end jobs just to save some cash-for-travel won't get 
            you very far - sure it works - but for how long? This way of life 
            sure aint gonna get easier as you get older.
          </p>
          <!-- You soon realize that you're not getting any younger and everyone around you is getting their sh!t together.</p> -->

          <p>
            <strong><em>What if you could travel (climb) around the world on your own terms?</em></strong><br> 
            Imagine working your own hours online as a freelancer, or selling products from your 
            online shop. You could live minutes from a world-class crag in Thailand, China, Greece or Spain,
            where a months rent could easily be made in a single working day! I call this <strong><em>Digital Dirtbagging</em></strong>. 
          </p>

          <p>
            <strong>Adventure In My Veins</strong> was created out my own struggles to figuring out financial and locational independence. 
            I built this site for anyone out there who wants to learn from experts across various digital and creative industries, and my first-hand experience in
            building a successful freelancing business.
          </p>

          <p>
            If you want to learn how to become a <strong><em>Digital Dirtbag</em></strong> then you’ve come to the perfect place. 
            So let me help you out. I'd be happy to take show you the <em>most important</em> steps you need to take to master location and financial freedom.
          </p>

          <ul>
            <li>Want to learn how to launch a website for your business / blog or personal brand? I've got tons of advice to help with that.</li>
            <li>Are you serious about your career but still want to travel, and climb often? Yep, that's entirely possible. I'll show you how.</li>
            <li>Like to take the plunge and become a freelancer? I can help you build a portfolio and attract high-paying clients.</li>
            <li>Want to connect with like-minds from around the world? The <strong style="text-decoration: underline; ">Digital Dirtbag Community</strong> is a great place to start!</li>
          </ul>

          <p>By joining the Digital Dirtbag Community you'll have access to all of this and so much more!</p>

          <p>
            And when you get the exact right information, you can immediately begin to take action. 
            And that’s what’s going to get you out of your dead-end job and into the mountains! 🏔
          </p>
<!--           
          <p>
            To kick things off, I'd love to send you my <strong>DIY Guide To Ditial Dirtbagging</strong>. 
            Just let me know where to send it by entering your details below - then you'll be subscribed to 
            the Digital Dirtbag Community where you'll get access to tons of other great tools to crush it as a Digital Dirtbag.
          </p> -->
        </div>

        <article class="mt-3">
          <mailchimp-form  />
        </article>
      </div>
    </article>
  </main>
</template>

<script>
import MailchimpForm from "@/components/MailchimpForm";

export default {
  components: {
    MailchimpForm
  }
};
</script>

<style lang="scss" scoped>
.intro {
  padding-top: 2rem;
  font-size: 1.15rem;

  &:first-child::first-letter {
    float: left;
    font-size: 70px;
    font-weight: normal;
    line-height: 60px;
    padding-top: 0;
    padding-right: 8px;
    padding-left: 0px;
  }
}
</style>