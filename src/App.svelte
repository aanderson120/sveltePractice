<script>
  import Modal from "./Modal.svelte";
  import AddPersonForm from "./AddPersonForm.svelte";
  let showModal = false;
  let toggleModal = () => {
    showModal = !showModal;
  };
  let people = [
    { name: "yoshi", beltColor: "black", age: 25, id: 1, skills: [] },
    { name: "mario", beltColor: "orange", age: 45, id: 2, skills: [] },
    { name: "luigi", beltColor: "brown", age: 35, id: 3, skills: [] },
  ];
  const handleClick = (e, id) => {
    people = people.filter((person) => person.id != id);
    console.log(e);
  };

  const addPerson = (e) => {
    // console.log(e.detail)
    const person = e.detail;
    people = [person, ...people];
    showModal = false;
  };
</script>

<Modal {showModal} on:click={toggleModal}>
  <AddPersonForm on:addPerson={addPerson} />
</Modal>

<main>
  <button on:click={toggleModal}>Open Modal</button>
  {#each people as person (person.id)}
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColor === "black"}
        <p><strong>Master Ninja</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColor} belt.</p>
      <ul>
        {#each person.skills as skill}
          <li>{skill}</li>
        {/each}
      </ul>
      <button on:click={(e) => handleClick(e, person.id)}>delete</button>
    </div>
  {:else}
    <p>There are no people to show...</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  ul {
    display: flex;
    flex-direction: column;
  }
  li {
    width: fit-content;
    align-self: center;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
