<script>
  export let setView;
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

  //links
  const externalLinks = [
    { title: 'Outlook', href: 'https://outlook.office.com/mail/', external: true },
    { title: 'Catalyst', href: 'https://classes.catalyst-services.uc.edu/search/', external: true },
    { title: 'Finances', view: 'finances', external: false},
    { title: 'My Grad Plan', href: '#', external: false }, //cant find a valid link rn
    { title: 'Build My Schedule', href: 'https://www.coursicle.com/college-schedule-maker/', external: true },
    { title: 'Teams', href: 'https://teams.microsoft.com/', external: true },
    { title: 'Canvas', href: 'https://uc.instructure.com/', external: true },
    { title: 'Campus Jobs', href: 'https://uc.joinhandshake.com/explore', external: true }
  ];


  import ucLogo from './assets/university_of_cincinnati-logo.webp';
</script>

<!--desktop-->
<aside class="hidden lg:flex lg:flex-col lg:w-72 bg-white border-r">
  <div class="p-6 flex flex-col h-full">
    <!--side for logo + name-->
    <div class="flex items-center gap-3 mb-6">
      <div class="w-11 h-10 flex items-center justify-center">
        <img src={ucLogo} alt="University of Cincinnati logo" class="w-11 h-10 object-contain" />
      </div>
      <div>
        <div class="text-lg font-semibold">Rania Maaraba</div>
        <div class="text-xs text-gray-500">Dashboard</div>
      </div>
    </div>

    <!--navi links-->
    <nav class="flex-1 space-y-1 text-sm">
      {#each externalLinks as l}
        {#if l.external}
          <a
            class="flex items-center gap-3 p-3 rounded hover:bg-gray-50"
            href={l.href}
            target="_blank"
            rel="noopener noreferrer"
          >
            <svg class="w-4 h-4 text-red-500" viewBox="0 0 20 20" fill="currentColor">
              <path d="M10 2a8 8 0 100 16 8 8 0 000-16z" />
            </svg>
            <span>{l.title}</span>
          </a>
        {:else}
          <button
            class="flex items-center gap-3 p-3 rounded hover:bg-gray-50 w-full text-left"
            on:click={() => setView(l.view)}
          >
            <svg class="w-4 h-4 text-red-500" viewBox="0 0 20 20" fill="currentColor">
              <path d="M10 2a8 8 0 100 16 8 8 0 000-16z" />
            </svg>
            <span>{l.title}</span>
          </button>
        {/if}
      {/each}
    </nav>

    <!--footer-->
    <div class="mt-6 text-xs text-gray-500">
      © University of Cincinnati — RM and MB
    </div>
  </div>
</aside>

<!--mobile-->
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
          {#each externalLinks as l}
            <a
              class="block p-2 rounded hover:bg-gray-50"
              href={l.href}
              target={l.external ? "_blank" : null}
              rel={l.external ? "noopener noreferrer" : null}
              on:click={() => open = false}
            >
              {l.title}
            </a>
          {/each}
        </nav>
      </div>
    </div>
  {/if}
</div>