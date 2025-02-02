<script lang="ts">
  import { icons } from '$assets';
  import { Button, FAQItem } from '$components';
  import { faqs } from '$data';

  let questionCurrentlyExpanded = $state(-1);

  function onclick(index: number) {
    if (index === questionCurrentlyExpanded) {
      questionCurrentlyExpanded = -1;
    } else {
      questionCurrentlyExpanded = index;
    }
  }
</script>

<section class="landing-page-section">
  <h2 class="mb-l">Frequently asked questions</h2>
  <div class="faq-container">
    {#each faqs as faq, index}
      <FAQItem
        {faq}
        isExpanded={index === questionCurrentlyExpanded}
        onclick={() => onclick(index)}
      />
    {/each}
  </div>
  <div class="additional-info mt-m">
    <Button class="mt-s">BUY NOW</Button>
    <p class="mt-m">Any other questions?</p>
    <a href="https://x.com/KIZO_ES">
      <p>
        Hit me up on twitter <img class="twitter-icon" src={icons.twitterIcon} alt="" />
      </p>
    </a>
  </div>
</section>

<style>
  .additional-info {
    display: flex;
    flex-direction: column;
    align-items: center;
    color: grey;
  }

  .additional-info a {
    text-decoration: underline;
  }

  .twitter-icon {
    width: 16px;
    height: 16px;
  }
</style>
