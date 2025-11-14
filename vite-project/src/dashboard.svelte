<script>
  export let setView;
  import uiLogo from './assets/ui-class.png';
  import aiLogo from './assets/ai-logo.jpg';
  import compEng from './assets/c-eng-logo.png';
  import compSys from './assets/computer-sys-logo.jpg';
  import calcLogo from './assets/calc-logo.png';
  import profilePic from './assets/rpfp.jpeg';

  //Student Stats
  const studentStats = [
    { label: 'Current GPA', value: '3.67', sublabel: 'Cumulative: 3.54',  color: 'bg-blue-50 border-blue-200 text-blue-600' },
    { label: 'Credits Earned', value: '89/120', sublabel: '31 credits remaining',  color: 'bg-green-50 border-green-200 text-green-600' },
    { label: 'Due This Week', value: '5', sublabel: '2 assignments, 3 events',  color: 'bg-red-50 border-red-200 text-red-600' },
    { label: 'Next Class', value: '2:30 PM', sublabel: 'Operating Systems',  color: 'bg-purple-50 border-purple-200 text-purple-600' }
  ];


  //Quick Access Links - make sure they link?
  const quickLinks = [
  { title: 'Canvas', description: 'View courses & assignments', color: 'bg-red-600', href: 'https://uc.instructure.com', external: true },
  { title: 'Catalyst', description: 'Register for classes', color: 'bg-orange-600', href: 'https://classes.catalyst-services.uc.edu/search/', external: true },
  { title: 'Outlook', description: 'Check university email', color: 'bg-blue-600', href: 'https://outlook.office.com/mail/', external: true },
  { title: 'My Grad Plan', description: 'Track degree progress', color: 'bg-green-600', view: 'calendar', external: false },
  { title: 'Finances', description: 'View balance & aid', color: 'bg-yellow-600', view: 'finances', external: false },
  { title: 'Campus Jobs', description: 'Find work opportunities', color: 'bg-indigo-600', href: 'https://uc.joinhandshake.com/explore', external: true }
];

  const classes = [
    { title: 'User Interfaces', code: 'CS 5167-001', teacher: 'Jillian Aurisano', posted: '12 hours ago', assignment: 'Group 4: Check-in!', due: 'Due Tuesday at 11:59 PM', logo: uiLogo, status: 'urgent' },
    { title: 'Artifical Intelligence', code: 'CS 4033-001', teacher: 'Anca Ralescu', posted: '2 day ago', assignment: 'Forward chaining, backward chaining and goal trees', due: 'Next Wednesday at 11:59 PM', logo: aiLogo, status: 'upcoming' },
    { title: 'Embedded System Design', code: 'EECE 4038C-004', teacher: 'Jon Lockhart', posted: '3 days ago', assignment: 'Reading 10.2 Modular Design', due: 'Tomorrow at 11:59', logo: compEng, status: 'urgent' },
    { title: 'Operating Systems', code: 'CS 4029-001', teacher: 'John Gallagher', posted: '1 week ago', assignment: 'big.c Lab', due: 'Next Friday at 11:59', logo: compSys, status: 'upcoming' },
    { title: 'Advanced Calculus II', code: 'MATH 5102-001', teacher: 'Lenoid Slavin', posted: '1 day ago', assignment: 'Homework VIII - Implicit functions and extrema', due: 'Thursday at 11:59', logo: calcLogo, status: 'upcoming' }
  ];

  const actionItems = [
    { type: 'assignment', title: 'UI Check-in Due', course: 'CS 5167', due: 'Today, 11:59 PM', priority: 'high' },
    { type: 'assignment', title: 'Embedded Systems Reading', course: 'EECE 4038C', due: 'Tomorrow, 11:59 PM', priority: 'high' },
    { type: 'event', title: 'Rocketry Club Meeting', location: 'BALDWIN 880', due: 'Today, 5:00 PM', priority: 'medium' },
    { type: 'registration', title: 'Spring 2026 Registration Opens', due: 'Nov 15, 8:00 AM', priority: 'medium' },
    { type: 'payment', title: 'Tuition Payment Due', due: 'Nov 15, 11:59 PM', priority: 'high' }
  ];

  const campusResources = [
    { title: 'Langsam Library', status: 'Open until 11:00 PM', hours: 'Extended hours this week' },
    { title: 'Rec Center', status: 'Open', hours: '6:00 AM - 11:00 PM'  },
    { title: 'TUC Food Court', status: 'Open', hours: 'Until 9:00 PM' },
    { title: 'Campus Shuttle', status: 'Running', hours: 'Next: 8 mins' }
  ];

  function getPriorityColor(priority) {
    switch(priority) {
      case 'high': return 'border-l-4 border-red-500 bg-red-50';
      case 'medium': return 'border-l-4 border-yellow-500 bg-yellow-50';
      default: return 'border-l-4 border-gray-300 bg-gray-50';
    }
  }

  function getTypeIcon(type) {
    switch(type) {
      case 'assignment': return '';
      case 'event': return '';
      case 'registration': return '';
      case 'payment': return '';
      default: return '';
    }
  }
</script>

<div class="max-w-7xl mx-auto space-y-6">
  <!----Student Profile Card-->
  <div class="bg-gradient-to-r from-red-600 to-red-700 text-white rounded-lg p-6 shadow-lg">
    <div class="flex items-center gap-4">
      <img src={profilePic} alt="Profile" class="w-20 h-20 rounded-full border-4 border-white shadow-lg object-cover" />
      <div class="flex-1">
        <h1 class="text-2xl font-bold">Welcome back, Rania!</h1>
        <p class="text-red-100 mt-1">Computer Science • Junior • Fall 2025</p>
        <p class="text-red-100 text-sm">Advisor: Dr. Sarah Johnson • Next Meeting: Nov 20</p>
      </div>
      <div class="text-right">
        <div class="text-3xl font-bold">3.67</div>
        <div class="text-sm text-red-100">Current GPA</div>
      </div>
    </div>
  </div>

  <!----Stats Grid -->
  <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4">
    {#each studentStats as stat}
      <div class="bg-white border-2 {stat.color} rounded-lg p-4 hover:shadow-md transition-shadow">
        <div class="flex items-start justify-between">
          <div class="flex-1">
            <div class="text-sm text-gray-600 mb-1">{stat.label}</div>
            <div class="text-3xl font-bold mb-1">{stat.value}</div>
            <div class="text-xs text-gray-500">{stat.sublabel}</div>
          </div>
          <div class="text-3xl">{stat.icon}</div>
        </div>
      </div>
    {/each}
  </div>

  <!----Quick Access Links - THE KEY FEATURE! -->
  <!-- why did you make this so aggresive lmao-->
  <div class="bg-white border rounded-lg p-6 shadow-sm">
    <h2 class="text-xl font-semibold mb-4 flex items-center gap-2">
      <span></span>
      Quick Access
      <span class="text-sm font-normal text-gray-500">(Most Used)</span>
    </h2>
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-4">
      {#each quickLinks as link}
        {#if link.external}
          <a 
            href={link.href}
            target="_blank"
            rel="noopener noreferrer"
            class="group p-4 rounded-lg border-2 border-gray-200 hover:border-red-500 hover:shadow-lg transition-all text-center"
          >
            <div class="text-4xl mb-2">{link.icon}</div>
            <div class="font-semibold text-sm mb-1">{link.title}</div>
            <div class="text-xs text-gray-500 group-hover:text-gray-700">{link.description}</div>
          </a>
        {:else}
          <button
            on:click={() => setView(link.view)}
            class="group p-4 rounded-lg border-2 border-gray-200 hover:border-red-500 hover:shadow-lg transition-all text-center w-full"
          >
            <div class="text-4xl mb-2">{link.icon}</div>
            <div class="font-semibold text-sm mb-1">{link.title}</div>
            <div class="text-xs text-gray-500 group-hover:text-gray-700">{link.description}</div>
          </button>
        {/if}
      {/each}
    </div>
  </div>

  <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
    <!----Main Column for Assignments and Classes -->
    <div class="lg:col-span-2 space-y-6">
      <!----Action Items and To-Do -->
      <div class="bg-white border rounded-lg p-6 shadow-sm">
        <h2 class="text-lg font-semibold mb-4 flex items-center gap-2">
          <span></span>
          Action Items
          <span class="ml-auto text-sm font-normal">
            <span class="px-2 py-1 bg-red-100 text-red-700 rounded-full text-xs">
              {actionItems.filter(i => i.priority === 'high').length} urgent
            </span>
          </span>
        </h2>
        <ul class="space-y-2">
          {#each actionItems as item}
            <li class="flex items-start gap-3 p-3 rounded {getPriorityColor(item.priority)} hover:shadow-sm transition-shadow">
              <div class="text-2xl">{getTypeIcon(item.type)}</div>
              <div class="flex-1 min-w-0">
                <div class="font-medium text-sm">{item.title}</div>
                <div class="text-xs text-gray-600 mt-1">
                  {#if item.course}
                    {item.course} • 
                  {/if}
                  {#if item.location}
                    {item.location} • 
                  {/if}
                  {item.due}
                </div>
              </div>
              <button class="px-3 py-1 text-xs bg-white border rounded hover:bg-gray-50 whitespace-nowrap">
                View
              </button>
            </li>
          {/each}
        </ul>
      </div>

      <!----Course Feed -->
      <div class="bg-white border rounded-lg p-6 shadow-sm">
        <h2 class="text-lg font-semibold mb-4">Recent Course Activity</h2>
        <ul class="space-y-4">
          {#each classes as c}
            <li class="flex gap-4 p-3 rounded hover:bg-gray-50 transition-colors border">
              <img src={c.logo} alt="course-logo" class="w-14 h-14 rounded object-cover flex-shrink-0" />
              <div class="flex-1 min-w-0">
                <div class="flex items-start justify-between gap-2 mb-1">
                  <div class="font-semibold text-sm">{c.title}</div>
                  <span class="text-xs text-gray-500 whitespace-nowrap">{c.posted}</span>
                </div>
                <div class="text-xs text-gray-500 mb-2">{c.code} • {c.teacher}</div>
                <div class="text-sm text-gray-700 mb-1">{c.assignment}</div>
                <div class="flex items-center justify-between">
                  <div class="text-xs {c.status === 'urgent' ? 'text-red-600 font-medium' : 'text-gray-600'}">
                    {c.due}
                  </div>
                  <a
                  href="https://uc.instructure.com"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="text-xs px-3 py-1 bg-red-600 text-white rounded hover:bg-red-700 inline-block text-center">
                    View in Canvas
                  </a>
                </div>
              </div>
            </li>
          {/each}
        </ul>
      </div>
    </div>

    <!----Right Sidebar -->
    <aside class="space-y-6">
      <!----Today's Schedule -->
      <div class="bg-white border rounded-lg p-6 shadow-sm">
        <h3 class="font-semibold mb-4 flex items-center gap-2">
          <span></span>
          Today's Schedule
          <span class="ml-auto text-xs text-gray-500">Thursday, Nov 7</span>
        </h3>
        <div class="space-y-3">
          <div class="flex gap-3 items-start p-2 bg-blue-50 rounded border border-blue-200">
            <div class="text-xs font-medium text-blue-700 whitespace-nowrap">9:00 AM</div>
            <div class="text-sm">
              <div class="font-medium">User Interfaces</div>
              <div class="text-xs text-gray-600">CS 5167 • Rhodes 750</div>
            </div>
          </div>
          <div class="flex gap-3 items-start p-2 bg-green-50 rounded border border-green-200">
            <div class="text-xs font-medium text-green-700 whitespace-nowrap">11:00 AM</div>
            <div class="text-sm">
              <div class="font-medium">Artificial Intelligence</div>
              <div class="text-xs text-gray-600">CS 4033 • Baldwin 680</div>
            </div>
          </div>
          <div class="flex gap-3 items-start p-2 bg-purple-50 rounded border border-purple-200">
            <div class="text-xs font-medium text-purple-700 whitespace-nowrap">1:00 PM</div>
            <div class="text-sm">
              <div class="font-medium">Embedded Systems</div>
              <div class="text-xs text-gray-600">EECE 4038C • ERC 240</div>
            </div>
          </div>
          <div class="flex gap-3 items-start p-2 bg-yellow-50 rounded border border-yellow-200">
            <div class="text-xs font-medium text-yellow-700 whitespace-nowrap">2:30 PM</div>
            <div class="text-sm">
              <div class="font-medium">Operating Systems</div>
              <div class="text-xs text-gray-600">CS 4029 • Rhodes 752</div>
            </div>
          </div>
          <div class="flex gap-3 items-start p-2 bg-red-50 rounded border border-red-200">
            <div class="text-xs font-medium text-red-700 whitespace-nowrap">5:00 PM</div>
            <div class="text-sm">
              <div class="font-medium">Rocketry Club Meeting</div>
              <div class="text-xs text-gray-600">Baldwin 880</div>
            </div>
          </div>
        </div>
        <button
        class="mt-4 w-full px-4 py-2 text-sm border rounded hover:bg-gray-50"
        on:click={() => setView('calendar')}>
        View Full Calendar
      </button>
      </div>

      <!----Campus Resources -->
      <div class="bg-white border rounded-lg p-6 shadow-sm">
        <h3 class="font-semibold mb-4 flex items-center gap-2">
          <span></span>
          Campus Resources
        </h3>
        <div class="space-y-3">
          {#each campusResources as resource}
            <div class="flex items-start gap-3 p-2 bg-gray-50 rounded">
              <div class="text-2xl">{resource.icon}</div>
              <div class="flex-1 min-w-0">
                <div class="font-medium text-sm">{resource.title}</div>
                <div class="text-xs text-green-600">{resource.status}</div>
                <div class="text-xs text-gray-500">{resource.hours}</div>
              </div>
            </div>
          {/each}
        </div>
      </div>

      <!----Bearcat Dollars Quick View -->
      <div class="bg-gradient-to-br from-green-500 to-green-600 text-white rounded-lg p-6 shadow-lg">
        <div class="flex items-center justify-between mb-2">
          <h3 class="font-semibold">Bearcat Dollars</h3>
          <span class="text-2xl"></span>
        </div>
        <div class="text-3xl font-bold mb-1">$127.50</div>
        <div class="text-sm text-green-100 mb-4">Available Balance</div>
        <button class="w-full px-4 py-2 bg-white text-green-600 rounded hover:bg-green-50 text-sm font-medium">
          Add Funds
        </button>
      </div>
    </aside>
  </div>
</div>