<script>
  import { isModalActive } from './stores.js';
</script>

<div class="modal {$isModalActive ? 'is-active' : ''}">
  <div class="modal-background" on:click={isModalActive.update}></div>
  <div class="modal-card">
    <header class="modal-card-head">
      <p class="modal-card-title">Modal title</p>
      <button class="delete" aria-label="close"></button>
    </header>
    <section class="modal-card-body">
      <!-- Content ... -->
    </section>
    <footer class="modal-card-foot">
      <button class="button is-success">Save changes</button>
      <button class="button">Cancel</button>
    </footer>
  </div>
</div>