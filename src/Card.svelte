<script>
  import { createEventDispatcher } from "svelte";
  export let id, name, lastName;

  const dispatch = createEventDispatcher();
  const baseUrl = "https://hr.oat.taocloud.org/v1/";

  const viewUser = () => dispatch("viewuser", id);
</script>

<article class="contact-card my">
  <h2>
    <slot>
      <span class="missing">{name.toUpperCase()}</span>
    </slot>
  </h2>

  <div class="address">
    <slot>
      <span class="missing">{lastName}</span>
    </slot>
  </div>

  <div class="email">
    <slot>
      <span class="missing">Id: {id}</span>
    </slot>
  </div>

  <button class="btn-success btn-sm btn" on:click={viewUser(id)}
    >See more...</button
  >
</article>

<style>
  .contact-card {
    width: 300px;
    border: 1px solid #aaa;
    border-radius: 15px;
    box-shadow: 2px 2px 8px rgba(0, 0, 0, 0.1);
    padding: 1em;
  }

  h2 {
    padding: 0 0 0.2em 0;
    margin: 0 0 1em 0;
    border-bottom: 1px solid #ff3e00;
  }

  .address,
  .email {
    padding: 0 0 0 1.5em;
    background: 0 50% no-repeat;
    background-size: 1em 1em;
    margin: 0 0 0.5em 0;
    line-height: 1.2;
  }

  .missing {
    color: #999;
  }
</style>
