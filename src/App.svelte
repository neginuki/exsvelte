<script>
  import { onMount } from "svelte";

  let data = [];

  onMount(async () => {
    const response = await fetch("http://localhost:8080/breweries/");
    data = await response.json();
  });
</script>

<style>

</style>

<main>
  蔵元一覧
  <table>
    <thead>
      <tr>
        <th>蔵名</th>
        <th>住所</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        {#each data as item}
          <td>{item.breweryName}({item.breweryNameKana})</td>
          <td>{item.address}</td>
        {/each}
      </tr>
    </tbody>
  </table>
</main>
