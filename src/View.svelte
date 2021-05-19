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
    <div class="contact-card">
      <header>
        <div class="thumb">
          <img src={response.picture} alt={response.lastName} />
        </div>
        <div class="user-data">
          <h1>{response.firstName}</h1>
          <h2>{response.lastName}</h2>
        </div>
      </header>
      <div class="description">
        <p>Email: {response.email}</p>
        <p>Address: {response.address}</p>
      </div>
    </div>
  </div>
{:catch error}
  <p>❌ There has been an error</p>
{/await}

<style>
  .contact-card {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    max-width: 30rem;
    border-radius: 5px;
    margin: 1rem 0;
  }

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 7rem;
  }

  .thumb {
    width: 33%;
    height: 100%;
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .user-data {
    width: 67%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    text-align: center;
    text-transform: capitalize;
  }

  h1 {
    font-size: 1.25rem;
    font-family: "Roboto Slab", sans-serif;
    margin: 0.5rem 0;
  }

  h2 {
    font-size: 1rem;
    font-weight: bold;
    color: #5a5a5a;
    margin: 0;
    margin-bottom: 0.5rem;
    text-align: center;
  }

  .description {
    border-top: 1px solid #ccc;
    padding: 1rem;
  }
</style>
