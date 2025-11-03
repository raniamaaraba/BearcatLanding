<script>
  let q = '';
</script>

<header class="bg-white border-b">
  <div class="max-w-7xl mx-auto px-4 py-4 flex items-center justify-between gap-4">
    <div class="flex items-center gap-4">
      <h1 class="text-xl font-semibold">Dashboard</h1>
      <div class="hidden sm:block">
        <input
          class="border rounded px-3 py-1 text-sm w-64 focus:outline-none focus:ring-2 focus:ring-indigo-200"
          placeholder="Search lessons or students"
          bind:value={q}
        />
      </div>
    </div>

    <div class="flex items-center gap-4">
      <button class="text-sm px-3 py-1 bg-red-600 text-white rounded">Finances</button>
      <div class="flex items-center gap-4">
      <button class="text-sm px-3 py-1 bg-red-600 text-white rounded">View Full Schedule</button>
      </div>
    </div>
  </div>
</header>
