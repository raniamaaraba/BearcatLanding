<script>
  let q = '';
  
  export let currentView = 'dashboard';
  export let setView;
  
  function getViewTitle(view) {
    switch(view) {
      case 'dashboard': return 'Dashboard';
      case 'calendar': return 'Schedule';
      case 'finances': return 'Finances';
      default: return 'Dashboard';
    }
  }
</script>

<header class="bg-white border-b">
  <div class="max-w-7xl mx-auto px-4 py-4 flex items-center justify-between gap-4">
    <div class="flex items-center gap-4">
      <h1 class="text-xl font-semibold">{getViewTitle(currentView)}</h1>
      <div class="hidden sm:block">
        <input
          class="border rounded px-3 py-1 text-sm w-64 focus:outline-none focus:ring-2 focus:ring-indigo-200"
          placeholder="Search lessons or students"
          bind:value={q}
        />
      </div>
    </div>

    <div class="flex items-center gap-2">
      <button 
        on:click={() => setView('finances')}
        class="text-sm px-3 py-1 {currentView === 'finances' ? 'bg-red-700' : 'bg-red-600'} text-white rounded hover:bg-red-700"
      >
        Finances
      </button>
      <button 
        on:click={() => setView('calendar')}
        class="text-sm px-3 py-1 {currentView === 'calendar' ? 'bg-red-700' : 'bg-red-600'} text-white rounded hover:bg-red-700"
      >
        Schedule
      </button>
      {#if currentView !== 'dashboard'}
        <button 
          on:click={() => setView('dashboard')}
          class="text-sm px-3 py-1 border rounded hover:bg-gray-50"
        >
          Dashboard
        </button>
      {/if}
    </div>
  </div>
</header>