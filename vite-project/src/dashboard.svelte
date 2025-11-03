<script>
  import uiLogo from './assets/ui-class.png';
  import aiLogo from './assets/ai-logo.jpg';
  import compEng from './assets/c-eng-logo.png';
  import compSys from './assets/computer-sys-logo.jpg';
  import calcLogo from './assets/calc-logo.png';


  const stats = [
    { label: 'Active Students', value: '1,248' },
    { label: 'New Enrollments', value: '87' },
    { label: 'Courses', value: '12' },
    { label: 'Avg Rating', value: '4.8' }
  ];

  const classes = [
    { title: 'User Interfaces', code: 'CS 5167-001', teacher: 'Jillian Aurisano', posted: '12 hours ago', assignment: 'Group 4: Check-in!', due: 'Due Tuesday at 11:59 PM', logo: uiLogo },
    { title: 'Artifical Intelligence', code: 'CS 4033-001', teacher: 'Anca Ralescu', posted: '2 day ago', assignment: 'Forward chaining, backward chaining and goal trees', due: 'Next Wednesday at 11:59 PM', logo: aiLogo },
    { title: 'Embedded System Design', code: 'EECE 4038C-004', teacher: 'Jon Lockhart', posted: '3 days ago', assignment: 'Reading 10.2 Modular Design' ,due: 'Tommorow at 11:59', logo:compEng },
    { title: 'Operating Systems', code: 'CS 4029-001', teacher: 'John Gallagher', posted: '1 week ago', assignment:'big.c Lab', due: 'Next Friday at 11:59', logo: compSys},
    { title: 'Advanced Calculus II', code: 'MATH 5102-001', teacher: 'Lenoid Slavin', posted: '1 day ago', assignment:'Homework VIII - Implicit functions and extrema', due:'Thursday at 11:59',logo: calcLogo}
  ];

  const activities = [
    { text: 'Assignment graded', who: 'S. Ramirez', when: '2 hrs ago' },
    { text: 'New enrollment', who: 'J. Lee', when: '5 hrs ago' },
    { text: 'Course updated', who: 'You', when: '1 day ago' }
  ];
</script>

<div class="max-w-7xl mx-auto grid grid-cols-1 lg:grid-cols-3 gap-6">
  <!-- main column -->
  <div class="lg:col-span-2 space-y-6">
    <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">
      {#each stats as s}
        <div class="bg-white border rounded p-4 flex items-center gap-4">
          <div class="p-3 bg-indigo-50 text-indigo-600 rounded">
            <svg class="w-6 h-6" viewBox="0 0 20 20" fill="currentColor"><path d="M10 2a8 8 0 100 16 8 8 0 000-16z" /></svg>
          </div>
          <div>
            <div class="text-xs text-gray-500">{s.label}</div>
            <div class="text-2xl font-semibold">{s.value}</div>
          </div>
        </div>
      {/each}
    </div>

    <div class="bg-white border rounded p-6">
      <h2 class="text-lg font-medium mb-4">Fall 2025: Courses</h2>
      <ul class="space-y-4">
        {#each classes as c}
          <li class="flex gap-4">
            <img src={c.logo} alt="course-logo" class="w-12 h-12 rounded object-cover" />
            <div class="flex-1">
              <div class="flex items-baseline justify-between">
                <div class="font-medium">{c.title} <span class="text-xs text-gray-500">• {c.code}</span></div>
                <div class="text-xs text-gray-500">{c.posted}</div>
              </div>
              <div class="text-sm text-gray-600 mt-1">{c.assignment}</div>
              <div class="text-sm text-gray-600 mt-1">{c.due}</div>
              <div class="text-xs text-gray-500 mt-2">{c.student} • via Canvas</div>
            </div>
          </li>
        {/each}
      </ul>
    </div>

    <div class="bg-white border rounded p-6">
      <h2 class="text-lg font-medium mb-4">Recent Activity</h2>
      <ul class="space-y-3">
        {#each activities as a}
          <li class="flex items-start gap-3">
            <div class="w-10 h-10 rounded bg-indigo-50 flex items-center justify-center text-indigo-600">U</div>
            <div class="flex-1 text-sm">
              <div class="font-medium">{a.text}</div>
              <div class="text-xs text-gray-500">{a.who} • {a.when}</div>
            </div>
          </li>
        {/each}
      </ul>
    </div>
  </div>

  <!-- right column -->
  <aside class="space-y-6">

    <div class="bg-white border rounded p-6">
      <h3 class="font-medium mb-3 text-2xl font-semibold">Upcoming Events</h3>
      <div class="text-sm text-gray-600 mt-1 ">Uptown Express Starts (every 45 min) • 08:30</div>
      <div class="text-sm text-gray-600 mt-1">COM Connector Starts (every 30 min) • 09:00</div>
      <div class="text-sm text-gray-600 mt-1">Northwest Starts (every 60 min) • 10:00</div>
      <div class="text-sm text-gray-600 mt-1">Northeast Starts (every 25 min) • 11:00</div>
      <div class="text-sm text-gray-600 mt-1">Rocketry Club Meeting • 17:00 BALDWIN 880 </div>
      <div class="text-sm text-gray-600 mt-1">Cincinnati Open House • 20:00 TUC 4032</div>
      <div class="text-sm text-gray-600 mt-1">Uptown Express Ends • 23:00</div>
      <div class="text-sm text-gray-600 mt-1">COM Connector Ends • 23:30</div>
      <div class="text-sm text-gray-600 mt-1">Northwest Ends • 23:30</div>
      <div class="text-sm text-gray-600 mt-1">Northeast Ends • 23:30</div>
    </div>

    <div class="bg-white border rounded p-6">
      <h3 class="font-medium mb-3 text-2xl font-semibold">Campus Resources</h3>
      <div class="">$3,420</div>
      <div class="text-sm text-gray-500 mt-2">Up 12% from last month</div>
    </div>
  </aside>
</div>
