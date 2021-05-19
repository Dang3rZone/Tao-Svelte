<script>
  import Card from "./Card.svelte";
  let value = "";
  // let loading = false;
  let response = [];
  let baseUrl = "https://hr.oat.taocloud.org/v1/";

  const handleInput = (event) => (value = event.target.value);

  $: if (value.length > 3) {
    fetch(`${baseUrl}users?name=${value}`)
      // .then(
      //   (res) =>
      //     !res.ok() &&
      //     new Error("Something bad happened with the fetching of users")
      // )
      .then((res) => res.json())
      .then((apiResponse) => (response = apiResponse || []));
    console.log(response);
  }
</script>

<input {value} on:input={handleInput} placeholder="Search user..." />

{#await response}
  <strong>Loading...</strong>
{:then response}
  {#each response as { userId: id, firstName: name, lastName }}
    <Card {id} {name} {lastName} />
  {:else}
    <strong>We have {response.length} users with that name</strong>
  {/each}
{:catch error}
  <p>❌ There has been an error</p>
{/await}
