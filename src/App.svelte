<script>
    import { onMount } from 'svelte';
    import GameHeader from './game/GameHeader.svelte';
    import History from './game/History.svelte';
    import GuessView from './game/GuessView.svelte';
    import Status from './game/Status.svelte';
    import StartGameButton from './game/StartGameButton.svelte';
    import GiveUpButton from './game/GiveUpButton.svelte';
    import Keypad from './game/Keypad.svelte';

    let guess = [];
    let statusMessage = '';
    let worker;

    onMount(() => {
        worker = new Worker('js/worker.js');
        worker.onmessage = receiveFromWorker;
    });

    function startGame() {
        worker.postMessage({ fn: 'startGame' });
    }

    function giveUp() {
        worker.postMessage({ fn: 'giveUp' });
    }

    function handleNumberPressed(number) {
        console.log('Number pressed', number);
    }

    function handleActionPressed(actionBtn) {
        console.log('Action pressed', actionBtn);
    }

    function updateStatus(message) {
        statusMessage = message;
    }

    function receiveFromWorker(message) {
        switch (message.data.fn) {
            case 'startGame':
                updateStatus(message.data.val);
                break;
            case 'giveUp':
                updateStatus(message.data.val);
                break;
            case 'guess':
                console.log('you guessed sth : S');
                break;
            default:
                break;
        }
    }
</script>

<div class="container">
    <GameHeader />
    <History />
    <GuessView />
    <Status message={statusMessage} />
    <div class="row mt-3">
        <StartGameButton on:click={startGame} />
        <GiveUpButton on:click={giveUp}/>
    </div>
    <hr />
    <Keypad on:numberPressed={handleNumberPressed} on:actionPressed={handleActionPressed} />
</div>
