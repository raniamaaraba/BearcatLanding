<script>
  import { onMount } from 'svelte';
  
  // Calendar state
  let currentDate = new Date();
  let selectedDate = null;
  let viewMode = 'month'; // 'month' or 'week'
  
  // Sample events - this would come from your data
  const events = [
    { date: new Date(2025, 10, 6), time: '08:30', title: 'Uptown Express Starts', type: 'shuttle', repeat: 'every 45 min' },
    { date: new Date(2025, 10, 6), time: '17:00', title: 'Rocketry Club Meeting', location: 'BALDWIN 880', type: 'club' },
    { date: new Date(2025, 10, 6), time: '20:00', title: 'Cincinnati Open House', location: 'TUC 4032', type: 'event' },
    { date: new Date(2025, 10, 11), time: '23:59', title: 'UI Design Check-in Due', type: 'assignment', course: 'CS 5167' },
    { date: new Date(2025, 10, 12), time: '23:59', title: 'AI Homework Due', type: 'assignment', course: 'CS 4033' },
    { date: new Date(2025, 10, 7), time: '23:59', title: 'Reading 10.2 Due', type: 'assignment', course: 'EECE 4038C' },
  ];
  
  // Classes schedule (MWF, TR patterns)
  const classSchedule = [
    { days: [1, 3, 5], time: '09:00-10:20', title: 'User Interfaces', code: 'CS 5167', color: 'bg-blue-100 border-blue-300' },
    { days: [2, 4], time: '11:00-12:20', title: 'AI', code: 'CS 4033', color: 'bg-green-100 border-green-300' },
    { days: [1, 3, 5], time: '13:00-14:20', title: 'Embedded Systems', code: 'EECE 4038C', color: 'bg-purple-100 border-purple-300' },
    { days: [2, 4], time: '14:30-15:50', title: 'Operating Systems', code: 'CS 4029', color: 'bg-yellow-100 border-yellow-300' },
    { days: [1, 3], time: '16:00-17:20', title: 'Advanced Calculus II', code: 'MATH 5102', color: 'bg-pink-100 border-pink-300' },
  ];
  
  $: monthStart = new Date(currentDate.getFullYear(), currentDate.getMonth(), 1);
  $: monthEnd = new Date(currentDate.getFullYear(), currentDate.getMonth() + 1, 0);
  $: monthName = currentDate.toLocaleDateString('en-US', { month: 'long', year: 'numeric' });
  
  // Generate calendar days
  $: calendarDays = generateCalendarDays(currentDate);
  
  function generateCalendarDays(date) {
    const year = date.getFullYear();
    const month = date.getMonth();
    const firstDay = new Date(year, month, 1);
    const lastDay = new Date(year, month + 1, 0);
    const startingDayOfWeek = firstDay.getDay();
    const daysInMonth = lastDay.getDate();
    
    const days = [];
    
    // Previous month's trailing days
    const prevMonthDays = new Date(year, month, 0).getDate();
    for (let i = startingDayOfWeek - 1; i >= 0; i--) {
      days.push({
        date: new Date(year, month - 1, prevMonthDays - i),
        isCurrentMonth: false
      });
    }
    
    // Current month days
    for (let i = 1; i <= daysInMonth; i++) {
      days.push({
        date: new Date(year, month, i),
        isCurrentMonth: true
      });
    }
    
    // Next month's leading days
    const remainingDays = 42 - days.length; // 6 rows × 7 days
    for (let i = 1; i <= remainingDays; i++) {
      days.push({
        date: new Date(year, month + 1, i),
        isCurrentMonth: false
      });
    }
    
    return days;
  }
  
  function getEventsForDate(date) {
    return events.filter(event => 
      event.date.toDateString() === date.toDateString()
    );
  }
  
  function getClassesForDate(date) {
    const dayOfWeek = date.getDay();
    return classSchedule.filter(cls => cls.days.includes(dayOfWeek));
  }
  
  function isToday(date) {
    const today = new Date();
    return date.toDateString() === today.toDateString();
  }
  
  function prevMonth() {
    currentDate = new Date(currentDate.getFullYear(), currentDate.getMonth() - 1, 1);
  }
  
  function nextMonth() {
    currentDate = new Date(currentDate.getFullYear(), currentDate.getMonth() + 1, 1);
  }
  
  function goToToday() {
    currentDate = new Date();
    selectedDate = new Date();
  }
  
  function selectDate(date) {
    selectedDate = date;
  }
  
  function getEventTypeColor(type) {
    switch(type) {
      case 'assignment': return 'bg-red-100 text-red-700 border-red-300';
      case 'club': return 'bg-purple-100 text-purple-700 border-purple-300';
      case 'shuttle': return 'bg-gray-100 text-gray-700 border-gray-300';
      case 'event': return 'bg-blue-100 text-blue-700 border-blue-300';
      default: return 'bg-gray-100 text-gray-700 border-gray-300';
    }
  }
</script>

<div class="bg-white border rounded-lg p-6">
  <! Calendar Header >
  <div class="flex items-center justify-between mb-6">
    <div class="flex items-center gap-4">
      <h2 class="text-2xl font-semibold">{monthName}</h2>
      <button 
        on:click={goToToday}
        class="px-3 py-1 text-sm bg-red-600 text-white rounded hover:bg-red-700"
      >
        Today
      </button>
    </div>
    
    <div class="flex items-center gap-2">
      <button 
        on:click={prevMonth}
        class="p-2 hover:bg-gray-100 rounded"
        aria-label="Previous month"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
        </svg>
      </button>
      <button 
        on:click={nextMonth}
        class="p-2 hover:bg-gray-100 rounded"
        aria-label="Next month"
      >
        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
        </svg>
      </button>
    </div>
  </div>
  
  <! Calendar Grid >
  <div class="grid grid-cols-7 gap-1">
    <! Day headers >
    {#each ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'] as day}
      <div class="text-center text-sm font-medium text-gray-600 py-2">
        {day}
      </div>
    {/each}
    
    <! Calendar days >
    {#each calendarDays as { date, isCurrentMonth }}
      {@const dayEvents = getEventsForDate(date)}
      {@const dayClasses = getClassesForDate(date)}
      {@const today = isToday(date)}
      {@const selected = selectedDate && date.toDateString() === selectedDate.toDateString()}
      
      <button
        on:click={() => selectDate(date)}
        class="min-h-[100px] p-2 border rounded hover:bg-gray-50 transition-colors text-left relative
               {!isCurrentMonth ? 'bg-gray-50 text-gray-400' : ''}
               {today ? 'ring-2 ring-red-500' : ''}
               {selected ? 'bg-red-50' : ''}"
      >
        <div class="text-sm font-medium mb-1 {today ? 'text-red-600' : ''}">
          {date.getDate()}
        </div>
        
        <! Classes for this day >
        {#if isCurrentMonth && dayClasses.length > 0}
          <div class="space-y-1">
            {#each dayClasses.slice(0, 2) as cls}
              <div class="text-xs p-1 rounded border {cls.color} truncate">
                {cls.code}
              </div>
            {/each}
            {#if dayClasses.length > 2}
              <div class="text-xs text-gray-500">+{dayClasses.length - 2} more</div>
            {/if}
          </div>
        {/if}
        
        <! Events for this day >
        {#if isCurrentMonth && dayEvents.length > 0}
          <div class="mt-1 space-y-1">
            {#each dayEvents.slice(0, 1) as event}
              <div class="text-xs p-1 rounded border {getEventTypeColor(event.type)} truncate">
                {event.title}
              </div>
            {/each}
            {#if dayEvents.length > 1}
              <div class="text-xs text-gray-500">+{dayEvents.length - 1} more</div>
            {/if}
          </div>
        {/if}
      </button>
    {/each}
  </div>
  
  <! Selected Date Details >
  {#if selectedDate}
    {@const selectedEvents = getEventsForDate(selectedDate)}
    {@const selectedClasses = getClassesForDate(selectedDate)}
    
    <div class="mt-6 p-4 bg-gray-50 rounded-lg border">
      <h3 class="text-lg font-medium mb-3">
        {selectedDate.toLocaleDateString('en-US', { weekday: 'long', month: 'long', day: 'numeric', year: 'numeric' })}
      </h3>
      
      {#if selectedClasses.length === 0 && selectedEvents.length === 0}
        <p class="text-sm text-gray-500">No classes or events scheduled</p>
      {/if}
      
      {#if selectedClasses.length > 0}
        <div class="mb-4">
          <h4 class="text-sm font-medium text-gray-700 mb-2">Classes</h4>
          <div class="space-y-2">
            {#each selectedClasses as cls}
              <div class="flex items-start gap-3 p-2 bg-white rounded border">
                <div class="text-sm font-medium text-gray-500">{cls.time}</div>
                <div class="flex-1">
                  <div class="text-sm font-medium">{cls.title}</div>
                  <div class="text-xs text-gray-500">{cls.code}</div>
                </div>
              </div>
            {/each}
          </div>
        </div>
      {/if}
      
      {#if selectedEvents.length > 0}
        <div>
          <h4 class="text-sm font-medium text-gray-700 mb-2">Events</h4>
          <div class="space-y-2">
            {#each selectedEvents as event}
              <div class="flex items-start gap-3 p-2 bg-white rounded border">
                <div class="text-sm font-medium text-gray-500">{event.time}</div>
                <div class="flex-1">
                  <div class="text-sm font-medium">{event.title}</div>
                  {#if event.location}
                    <div class="text-xs text-gray-500">📍 {event.location}</div>
                  {/if}
                  {#if event.course}
                    <div class="text-xs text-gray-500">📚 {event.course}</div>
                  {/if}
                  {#if event.repeat}
                    <div class="text-xs text-gray-500">🔄 {event.repeat}</div>
                  {/if}
                </div>
              </div>
            {/each}
          </div>
        </div>
      {/if}
    </div>
  {/if}
  
  <! Legend >
  <div class="mt-6 flex flex-wrap gap-4 text-xs">
    <div class="flex items-center gap-2">
      <div class="w-4 h-4 bg-red-100 border border-red-300 rounded"></div>
      <span>Assignments</span>
    </div>
    <div class="flex items-center gap-2">
      <div class="w-4 h-4 bg-blue-100 border border-blue-300 rounded"></div>
      <span>Classes</span>
    </div>
    <div class="flex items-center gap-2">
      <div class="w-4 h-4 bg-purple-100 border border-purple-300 rounded"></div>
      <span>Club Events</span>
    </div>
    <div class="flex items-center gap-2">
      <div class="w-4 h-4 bg-gray-100 border border-gray-300 rounded"></div>
      <span>Shuttle Schedule</span>
    </div>
  </div>
</div>