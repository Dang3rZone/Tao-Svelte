<script>
  import Card from "./Card.svelte";

  let value = "";
  let response = [];

  fetch("https://hr.oat.taocloud.org/v1/users")
    .then((res) => res.json())
    .then((apiResponse) => {
      response = apiResponse || [];
    });
</script>

{#each response as { userId: id, firstName: name, lastName }}
  <Card {id} {name} {lastName} />
{/each}
