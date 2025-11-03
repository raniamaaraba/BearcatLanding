<script>
  let open = false;
  const links = [
    { title: 'Outlook', href: '#' },
    { title: 'Catalyst', href: '#' },
    { title: 'Finances', href: '#' },
    { title: 'My Grad Plan', href: '#' },
    { title: 'Build My Schedule', href: '#' },
    { title: 'Teams', href: '#' },
    { title: 'Canvas', href: '#' },
    { title: 'Campus Jobs', href: '#' }
  ];

  import ucLogo from './assets/university_of_cincinnati-logo.webp';
</script>

<!-- Desktop -->
<aside class="hidden lg:flex lg:flex-col lg:w-72 bg-white border-r">
  <div class="p-6 flex flex-col h-full">
    <div class="flex items-center gap-3 mb-6">
      <div class="w-11 h-10 flex items-center justify-center">
          <img src={ucLogo} alt="University of Cincinnati logo" class="w-11 h-10" /> 
        </div>
      <div>
        <div class="text-lg font-semibold">Rania Maaraba</div>
        <div class="text-xs text-gray-500">Dashboard</div>
      </div>
    </div>

    <nav class="flex-1 space-y-1 text-sm">
      {#each links as l}
        <a class="flex items-center gap-3 p-3 rounded hover:bg-gray-50" href={l.href}>
          <svg class="w-4 h-4 text-red-500" viewBox="0 0 20 20" fill="currentColor">
            <path d="M10 2a8 8 0 100 16 8 8 0 000-16z" />
          </svg>
          <span>{l.title}</span>
        </a>
      {/each}
    </nav>

    <div class="mt-6 text-xs text-gray-500">
      © University of Cincinnati - RM and MB
    </div>
  </div>
</aside>


<!-- Mobile header + drawer -->
<div class="lg:hidden w-full">
  <div class="flex items-center justify-between p-4 bg-white border-b">
    <div class="flex items-center gap-3">
        <img src={ucLogo} alt="University of Cincinnati logo" class="w-10 h-10 rounded object-cover" />
      <div class="text-base font-semibold">Student</div>
    </div>
    <button class="px-3 py-2 bg-indigo-600 text-white rounded" on:click={() => open = !open}>Menu</button>
  </div>

  {#if open}
    <div class="absolute inset-x-4 top-20 z-50 bg-white border rounded shadow-lg">
      <div class="p-4">
        <nav class="space-y-2 text-sm">

        </nav>
      </div>
    </div>
  {/if}
</div>
