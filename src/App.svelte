<script>
  import Modal from "./Modal.svelte";

  let showModal = false;
  const toggleModal = () => {
    showModal = !showModal;
  };

  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1 },
    { name: "mario", beltColor: "orange", age: 45, id: 2 },
    { name: "luigi", beltColor: "brown", age: 35, id: 3 },
  ];
  const handleClick = (id) => {
    //delete the person from people
    people = people.filter((person) => person.id != id);
  };
</script>

<Modal isPromo={false} {showModal} on:click={toggleModal}>
  <h3>Add a New Person</h3>
  <form>
    <input type="text" placeholder="name" />
    <input type="text" placeholder="belt color" />
    <button>Add Person</button>
  </form>
</Modal>


<main>
  <button on:click|once={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor === "black"}
        <p><strong>Master Ninja</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColor} belt.</p>
      <button on:click={() => handleClick(person.id)}>Delete</button>
    </div>
  {:else}
    <p>There are no people to show at the moment.</p>
  {/each}
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
