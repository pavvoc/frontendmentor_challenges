<script>
  export let id; 
  export let logo; 
  export let company;
  export let isNew;
  export let isFeatured;
  export let position;
  export let postedAt;
  export let contract;
  export let location;
  export let role;
  export let level;
  export let languages;
  export let tools;

  // highlight first 2 cards
  let isHighlighted = id < 3 ? ' border-highlighted' : '';
</script>
<div class="job-card{isHighlighted}">
  <div class="company-logo">
    <img class="company-logo_img" src={logo} alt="{company} logo.">
  </div>
  <div class="job-info">
    <p class="t-company-name">{company}</p>
    {#if isNew}<p class="job-tag job-tag--new">new!</p>{/if}
    {#if isFeatured}<p class="job-tag job-tag--featured">featured</p>{/if}
    <p class="t-position position">{position}</p>
    <div class="other-info">
      <p>{postedAt}</p>
      <div class="dot-spacer"></div>
      <p>{contract}</p>
      <div class="dot-spacer"></div>
      <p>{location}</p>
    </div>
  </div>
  <div class="line-divider"></div>
  <div class="role-level-languages">
    <div class="keyword">
      {role}
    </div>
    <div class="keyword">
      {level}
    </div>
    {#each languages as language}
    <div class="keyword">
      {language}
    </div>
    {/each}
    {#each tools as tool}
    <div class="keyword">
      {tool}
    </div>
    {/each}
  </div>
</div>

<style type="text/scss">
  .company-logo {
    display: flex;
    @media (min-width: 640px) {
      display: inline-flex;
    }
  }
  .company-logo_img {
    width: 4.8rem;
    height: 4.8rem;
    transform: translateY(-50%);
    @media (min-width: 640px) {
      width: 8.8rem;
      height: 8.8rem;
      transform: translateY(0);
    }
  }
  .job-card {
    cursor: pointer;
    background-color: var(--color-white);
    border-radius: .5rem;
    padding: 0 2.4rem 2.4rem 1.9rem;
    border-left: .5rem solid transparent;
    box-shadow: 0 1.5rem 2rem -.5rem var(--color-card-shadow);
    transition: var(--transition) border-color;
    &:hover {
      border-color: var(--color-dark-cyan);
    }
    
    // highlight first 2 cards
    &.border-highlighted {
      border-color: var(--color-dark-cyan);
    }

    @media (min-width: 640px) {
      padding: 3.2rem 4rem 3.2rem 3.5rem;
    }
  }

  .job-card:not(:last-of-type) {
    margin-bottom: 4rem;
    @media (min-width: 640px) {
      margin-bottom: 2.4rem;
    }
  }

  .job-tag {
    font-size: 1.1rem;
    line-height: 1.4rem;
    font-weight: var(--weight-bold);
    letter-spacing: -0.08px;
    text-transform: uppercase;
    padding: .7rem .8rem .3rem;
    border-radius: 1.2rem;
    display: inline-block;
    color: var(--color-white);
    margin-right: .8rem;
    &--new {
      background-color: #5CA5A5;
    }
    &--featured {
      background-color: #2B3939;
    }
  }

  .job-info {
    margin-top: -1.1rem;
    @media (min-width: 640px) {
      margin-top: 0;
      display: inline-block;
      margin-left: 2.4rem;
    }
    .position {
      margin: .8rem 0;
    }
  }

  .dot-spacer {
    height: .4rem;
    width: .4rem;
    background-color: #B7C4C4;
    border-radius: 50%;
    margin: 0 .8rem;
  }

  .line-divider {
    @media (max-width: 960px) {
      height: .1rem;
      background-color: #B7C4C4;
      width: 100%;
      margin-top: 1.6rem;
    }
  }

  .other-info {
    color: #7C8F8F;
    font-weight: var(--weight-medium);
    font-size: 1.3rem;
    line-height: 2.4rem;
    letter-spacing: -.1px;
    display: inline-flex;
    align-items: center;
    @media (min-width: 640px) {
      font-size: 1.5rem;
      letter-spacing: -.12px;
    }
  }

  .role-level-languages {
    display: flex;
    flex-wrap: wrap;
  }

  .keyword {
    display: inline-block;
    color: var(--color-dark-cyan);
    background-color: #EEF6F6;
    padding: .4rem .8rem;
    font-size: 1.3rem;
    line-height: 2.4rem;
    letter-spacing: -.1px;
    font-weight: var(--weight-bold);
    border-radius: .4rem;
    margin-right: 1.4rem;
    margin-top: 1.6rem;
  }
</style>