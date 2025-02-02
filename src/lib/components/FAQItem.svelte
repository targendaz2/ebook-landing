<script lang="ts">
  import { icons } from '$assets';
  import type { faqs } from '$data';

  type FAQ = (typeof faqs)[number];

  interface Props {
    faq: FAQ;
    isExpanded?: boolean;
    onclick: () => void;
  }

  let { faq, isExpanded = false, onclick }: Props = $props();
</script>

<button class="container" class:container-expanded={isExpanded} {onclick}>
  <div class="question-and-answer">
    <p class="question mb-s">{faq.question}</p>
    <p class="answer">{faq.answer}</p>
  </div>
  <img src={icons.chevronDown} alt="" />
</button>

<style>
  .container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    padding: 12px 0;
    border-bottom: 1px solid grey;
    text-align: left;
  }

  .question-and-answer {
    padding-right: 150px;
  }

  .question {
    font-weight: 600;
  }

  .answer {
    max-height: 0;
    overflow: hidden;
    opacity: 0;
    transition:
      max-height 0.3s ease-out,
      opacity 0.3s ease-out;
  }

  .container-expanded .answer {
    max-height: unset;
    opacity: 1;
  }

  button img {
    width: 24px;
    height: 24px;
    transition: transform 0.3s linear;
  }

  .container-expanded img {
    transform: rotate(180deg);
  }
</style>
