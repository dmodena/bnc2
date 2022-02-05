<style>
    .history-container {
        height: 160px;
        overflow-y: scroll;
    }
</style>

<script>
    const bull = `<i class="bi bi-plus-circle"></i> `;
    const cow = `<i class="bi bi-dash-circle"></i> `;
    const none = `<i class="bi bi-dash-lg"></i> `;
    let history = '';

    function getBullsAndCows(feedback) {
        let result = '';

        feedback.filter(x => x == 1).forEach(x => result += bull);
        feedback.filter(x => x == 0).forEach(x => result += cow);

        if (result.length == 0)
            result += none;

        return result;
    }

    export function receiveHistory(guessAttempt, guess, feedback) {
        const bullsAndCows = getBullsAndCows(feedback);
        const newHistoryItem = `<li class="list-group-item">${guessAttempt}. ${guess}: ${bullsAndCows}</li>`;
        const oldHistory = history;
        history = newHistoryItem + oldHistory;
    }
</script>

<div class="row">
    <div class="col-12">
    <div class="card">
        <div class="card-header">History</div>
        <div class="history-container">
            <ul id="historyList" class="list-group list-group-flush">{@html history}</ul>
        </div>
    </div>
    </div>
</div>
