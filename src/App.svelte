<script>
    import GameHeader from './game/GameHeader.svelte';
    import History from './game/History.svelte';
    import GuessView from './game/GuessView.svelte';
    import Status from './game/Status.svelte';
    import StartGameButton from './game/StartGameButton.svelte';
    import GiveUpButton from './game/GiveUpButton.svelte';
    import Keypad from './game/Keypad.svelte';

    let guess = [];
</script>

<div class="container">
    <GameHeader />
    <History />
    <GuessView />
    <Status />
    <div class="row mt-3">
        <StartGameButton />
        <GiveUpButton />
    </div>
    <hr />
    <Keypad />
</div>
