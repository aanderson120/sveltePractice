<script>
  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "orange", age: 45, id: 2 },
    { name: "luigi", beltColor: "brown", age: 35, id: 3 },
  ];
</script>

<main>
  <!-- each loop -->
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      <p>{person.age} years old, {person.beltColor} belt.</p>
    </div>
  {:else}
    <p>There are no people to show at the moment.</p>
  {/each}
  <!-- same as 
	  <div>
    <h4>{people[0].name}</h4>
    <p>{people[0].beltColor}</p>
  </div>
  <div>
    <h4>{people[1].name}</h4>
    <p>{people[1].beltColor}</p>
  </div>
  <div>
    <h4>{people[2].name}</h4>
    <p>{people[2].beltColor}</p>
  </div> -->
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
