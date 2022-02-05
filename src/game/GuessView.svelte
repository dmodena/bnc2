<style>
    input {
        color: dimgray;
    }
</style>

<script>
    export let guess = [];
</script>

<div class="row mt-3">
    <div class="col-3">
    <input type="text" class="guess-input-view form-control text-center" value={guess[0] ?? ''} disabled>
    </div>
    <div class="col-3">
    <input type="text" class="guess-input-view form-control text-center" value={guess[1] ?? ''} disabled>
    </div>
    <div class="col-3">
    <input type="text" class="guess-input-view form-control text-center" value={guess[2] ?? ''} disabled>
    </div>
    <div class="col-3">
    <input type="text" class="guess-input-view form-control text-center" value={guess[3] ?? ''} disabled>
    </div>
    <input type="hidden" name="guessInput" id="guessInput">
</div>
