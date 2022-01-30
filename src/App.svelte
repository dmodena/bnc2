<script>
    import GameHeader from './game/GameHeader.svelte';
    import History from './game/History.svelte';
    import GuessView from './game/GuessView.svelte';
    import Status from './game/Status.svelte';
    import ControlButtons from './game/ControlButtons.svelte';
    import Keypad from './game/Keypad.svelte';
</script>

<div class="container">
    <GameHeader />
    <History />
    <GuessView />
    <Status />
    <ControlButtons />
    <hr />
    <Keypad />
</div>
