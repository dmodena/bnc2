<style>
    input {
        color: dimgray;
    }
</style>

<script>
    export let message = '';
</script>

<div class="row mt-3">
    <div class="col-12">
    <label for="statusInput">Status</label>
    <input type="text" class="form-control" id="statusInput" value={message} disabled>
    </div>
</div>
