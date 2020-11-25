<script>

  // Data
  const places = [
    {
      name: 'A Lama',
      icon: 'fa-chess-king',
      patrimonio: true,
      senderismo: true,
      museos: false,
      festas: true
    },
    {
      name: 'Barro',
      icon: 'fa-chess-knight',
      patrimonio: false,
      senderismo: true,
      museos: false,
      festas: true
    },
    {
      name: 'Campo Lameiro',
      icon: 'fa-chess-pawn',
      patrimonio: true,
      senderismo: false,
      museos: false,
      festas: true
    },
    {
      name: 'Cerdedo - Cotobade',
      icon: 'fa-chess-queen',
      patrimonio: false,
      senderismo: true,
      museos: false,
      festas: true
    },
    {
      name: 'Marín',
      icon: 'fa-chess-rook',
      patrimonio: true,
      senderismo: true,
      museos: false,
      festas: true
    },
    {
      name: 'Poio',
      icon: 'fa-chess-bishop',
      patrimonio: true,
      senderismo: false,
      museos: false,
      festas: false
    },
    {
      name: 'Ponte Caldelas',
      icon: 'fa-cheese',
      patrimonio: false,
      senderismo: true,
      museos: false,
      festas: true
    },
    {
      name: 'Pontevedra',
      icon: 'fa-pepper-hot',
      patrimonio: true,
      senderismo: true,
      museos: true,
      festas: true
    },
    {
      name: 'Vilaboa',
      icon: 'fa-fish',
      patrimonio: true,
      senderismo: true,
      museos: true,
      festas: true
    }
  ];

  // Variables
  let placesFiltered = places;
  let isModalActive = false;
  let searchOptions = {
    inputString: '',
    patrimonio: false,
    senderismo: false,
    museos: false,
    festas: false
  }

  const filterPlaces = () => {
    console.log(searchOptions)
    placesFiltered = places.filter((e) => {
      
      let one = true;
      let two = true;
      let three = true;
      let four = true;
      let five = true;

      if(!e.name.toLowerCase().includes(searchOptions.inputString.toLowerCase())) {
        one = false;
      }

      if(searchOptions.patrimonio && !e.patrimonio) {
        two = false;
      }

      if(searchOptions.senderismo && !e.senderismo) {
        three = false;
      }

      if(searchOptions.museos && !e.museos) {
        four = false;
      }

      if(searchOptions.festas && !e.festas) {
        five = false;
      }

      return one && two && three && four && five;
    });
  }

  const change = () => {
    filterPlaces();
  };

  filterPlaces();
  
</script>

<article class="panel is-success">
  <p class="panel-heading">
    Destinos
  </p>
  <div class="panel-block">
    <p class="control has-icons-left">
      <input bind:value={searchOptions.inputString} class="input is-success" type="text" placeholder="Búsqueda por concello" on:keyup="{change}">
      <span class="icon is-left">
        <i class="fas fa-search" aria-hidden="true"></i>
      </span>
    </p>
    <div class="checkboxes-wrapper">
      <label class="checkbox">
        <input bind:checked={searchOptions.patrimonio} type="checkbox" on:change="{change}">
        Patrimonio
      </label>
      <label class="checkbox">
        <input  bind:checked={searchOptions.senderismo} type="checkbox" on:change="{change}">
        Senderismo
      </label>
      <label class="checkbox">
        <input bind:checked={searchOptions.museos} type="checkbox" on:change="{change}">
        Museos
      </label>
      <label class="checkbox">
        <input bind:checked={searchOptions.festas} type="checkbox" on:change="{change}">
        Festas
      </label>
    </div>
  </div>
  {#each placesFiltered as { name, icon }, i}
    <a href="#" class="panel-block is-active" on:click="{isModalActive.update}">
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

.panel-block {
  flex-wrap: wrap;
  width: 100%;
}

.checkboxes-wrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 100%;
  padding-top: 0.75rem;
}

.checkbox {
  width: 50%;
  padding-top: 0.75rem;
  padding-left: 0.75rem;
}

@media (max-width: 900px) {
  article {
    width: 100%;
  }
}
</style>