<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    function numberPressed(number) {
        dispatch('numberPressed', number);
    }

    function actionPressed(actionBtn) {
        dispatch('actionPressed', actionBtn);
    }
</script>

<div id="keypad" class="mb-5">
    <div class="row mt-3">
      <div class="d-grid col-4">
        <button id="numBtn1" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(1)}>1</button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn2" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(2)}>2</button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn3" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(3)}>3</button>
      </div>
    </div>
    <div class="row mt-2">
      <div class="d-grid col-4">
        <button id="numBtn4" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(4)}>4</button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn5" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(5)}>5</button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn6" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(6)}>6</button>
      </div>
    </div>
    <div class="row mt-2">
      <div class="d-grid col-4">
        <button id="numBtn7" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(7)}>7</button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn8" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(8)}>8</button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn9" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(9)}>9</button>
      </div>
    </div>
    <div class="row mt-2">
    <div class="d-grid col-4">
        <button id="guessBtn" class="btn btn-outline-success" type="button" on:click={() => actionPressed('Submit')}><i class="bi bi-check2"></i></button>
      </div>
      <div class="d-grid col-4">
        <button id="numBtn0" class="btn btn-outline-secondary" type="button" on:click={() => numberPressed(0)}>0</button>
      </div>
      <div class="d-grid col-4">
        <button id="backspaceBtn" class="btn btn-outline-danger" type="button" on:click={() => actionPressed('Backspace')}><i class="bi bi-arrow-left"></i></button>
      </div>
    </div>
</div>
