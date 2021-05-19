<script>
  export let id;
  let response = [];
  const baseUrl = "https://hr.oat.taocloud.org/v1/";

  fetch(`${baseUrl}user/${id}`)
    .then((res) => res.json())
    .then((apiResponse) => {
      response = apiResponse || [];
      console.log("este es el response", response);
    });
</script>

<h2>User View</h2>
{#await response}
  <strong>Loading...</strong>
{:then response}
  <div class="card grid-1">
    <img src={response.picture} alt={response.lastName} class="round-img" />
    <h2>
      {response.title}.
      <strong>{response.firstName}</strong>
      {response.lastName}
    </h2>
  </div>
  <div class="card">
    <ul>
      <li>Email: {response.email}</li>
      <li>Address: {response.address}</li>
      <li>Gender: {response.gender}</li>
    </ul>
  </div>
{:catch error}
  <p>❌ There has been an error</p>
{/await}
