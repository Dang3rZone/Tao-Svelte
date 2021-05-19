<script>
  import Card from "./Card.svelte";

  let value = "";
  let response = [];

  const baseUrl = "https://hr.oat.taocloud.org/v1/";

  fetch(`${baseUrl}users`)
    .then((res) => res.json())
    .then((apiResponse) => {
      response = apiResponse || [];
    });
</script>

{#each response as { userId: id, firstName: name, lastName }}
  <!-- <Card {id} {name} {lastName} on:viewuser={viewUser(id)} /> -->
  <Card {id} {name} {lastName} />
{/each}
