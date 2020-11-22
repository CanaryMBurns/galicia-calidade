<script>
  // Data
  const places = [
    {
      name: 'Vigo',
      icon: 'fa-chess-king',
      hasVeganFood: true,
      hasBeach: true
    },
    {
      name: 'Lugo',
      icon: 'fa-chess-knight',
      hasVeganFood: false,
      hasBeach: false
    },
    {
      name: 'Santiago de Compostela',
      icon: 'fa-chess-pawn',
      hasVeganFood: true,
      hasBeach: false
    },
    {
      name: 'Ourense',
      icon: 'fa-chess-queen',
      hasVeganFood: false,
      hasBeach: false
    },
    {
      name: 'A coruña',
      icon: 'fa-chess-rook',
      hasVeganFood: true,
      hasBeach: true
    },
    {
      name: 'Ferrol',
      icon: 'fa-chess-bishop',
      hasVeganFood: false,
      hasBeach: true
    }
  ];

  // Variables
  let placesFiltered = places;
  let inputString = '';

  const filterPlaces = () => {
    placesFiltered = places.filter((e) => { return e.name.toLowerCase().includes(inputString.toLowerCase()); });
  }

  const keyUp = () => {
    filterPlaces();
  };
  
</script>

<article class="panel is-success">
  <p class="panel-heading">
    Places
  </p>
  <div class="panel-block">
    <p class="control has-icons-left">
      <input bind:value={inputString} class="input is-success" type="text" placeholder="Search by name" on:keyup="{keyUp}">
      <span class="icon is-left">
        <i class="fas fa-search" aria-hidden="true"></i>
      </span>
    </p>
  </div>
  {#each placesFiltered as { name, icon }, i}
    <a href="#" class="panel-block is-active">
      <span class="panel-icon">
        <i class="fas {icon}" aria-hidden="true"></i>
      </span>
      {name}
    </a>
	{/each}
</article>

<style>
article {
  width: 50%;
  background-color: white;
}

@media (max-width: 900px) {
  article {
    width: 100%;
  }
}
</style>