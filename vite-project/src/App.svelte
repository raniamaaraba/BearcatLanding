<script>
  import Sidebar from './sidebar.svelte';
  import Dashboard from './dashboard.svelte';
  import Calendar from './calendar.svelte';
  import Finances from './finances.svelte';
  import Header from './header.svelte';
  
  let currentView = 'dashboard';
  
  function setView(view) {
    currentView = view;
  }

</script>

<!-- updating for navigation for sidebar-->
<div class="min-h-screen bg-gray-50 text-gray-800">
  <div class="flex">
    <Sidebar {setView} />
    <div class="flex-1">
      <Header {currentView} {setView} />
      <main class="p-6 lg:p-8">
        {#if currentView === 'dashboard'}
          <Dashboard {setView} />
        {:else if currentView === 'calendar'}
          <Calendar />
        {:else if currentView === 'finances'}
          <Finances />
        {/if}
      </main>
    </div>
  </div>
</div>
