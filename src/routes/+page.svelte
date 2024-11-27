<script>
  import { getCurrentWebviewWindow } from '@tauri-apps/api/webviewWindow';
  import { emitTo, TauriEvent } from '@tauri-apps/api/event'

  const currentWin = getCurrentWebviewWindow()

  currentWin.listen(TauriEvent.WINDOW_CLOSE_REQUESTED, async _ => {
    // ...

    currentWin.destroy()
  })

  function close() {
    emitTo(currentWin.label, TauriEvent.WINDOW_CLOSE_REQUESTED);
  }
</script>

<main class="container">
  <h1>Welcome to Tauri + Svelte</h1>
  <button style="font-size: 16px;" on:click={close}>Close Window</button>
</main>

<style>
  h1 {
    text-align: center;
  }
</style>
