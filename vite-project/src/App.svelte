<script>
  //inital set-up based on https://www.creative-tim.com/twcomponents/component/tailwind-teacher-dashboard
  import Sidebar from './sidebar.svelte';
  import Dashboard from './dashboard.svelte';
  import Header from './header.svelte';
</script>

<div class="min-h-screen bg-gray-50 text-gray-800">
  <div class="flex">
    <Sidebar />
    <div class="flex-1">
      <Header />
      <main class="p-6 lg:p-8">
        <Dashboard />
      </main>
    </div>
  </div>
</div>

