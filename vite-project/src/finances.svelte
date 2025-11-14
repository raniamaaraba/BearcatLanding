<script>
  let selectedSemester = 'fall2025';
  
  const accountSummary = {
    balance: 3420.50,
    dueDate: 'November 15, 2025',
    nextPayment: 1710.25
  };
  
  const tuitionBreakdown = {
    fall2025: {
      tuition: 5840.00,
      fees: 680.00,
      housing: 3200.00,
      mealPlan: 1500.00,
      total: 11220.00,
      paid: 7799.50,
      remaining: 3420.50
    },
    spring2025: {
      tuition: 5840.00,
      fees: 680.00,
      housing: 3200.00,
      mealPlan: 1500.00,
      total: 11220.00,
      paid: 11220.00,
      remaining: 0.00
    }
  };
  
  const financialAid = [
    { type: 'Federal Pell Grant', amount: 3500.00, status: 'Disbursed', date: 'Aug 15, 2025' },
    { type: 'UC Scholarship', amount: 2000.00, status: 'Disbursed', date: 'Aug 15, 2025' },
    { type: 'Student Loan', amount: 5000.00, status: 'Pending', date: 'Nov 1, 2025' },
    { type: 'Work Study', amount: 1200.00, status: 'In Progress', date: 'Ongoing' }
  ];
  
  const paymentHistory = [
    { date: 'Sep 15, 2025', description: 'Tuition Payment - Fall 2025', amount: -2500.00, balance: 8720.50 },
    { date: 'Sep 10, 2025', description: 'Financial Aid Disbursement', amount: 5500.00, balance: 11220.50 },
    { date: 'Aug 20, 2025', description: 'Housing Deposit', amount: -500.00, balance: 5720.50 },
    { date: 'Aug 15, 2025', description: 'Tuition Charge - Fall 2025', amount: -11220.00, balance: 6220.50 },
    { date: 'May 15, 2025', description: 'Spring 2025 Final Payment', amount: -2200.00, balance: 17440.50 }
  ];
  
  const upcomingPayments = [
    { date: 'Nov 15, 2025', description: 'Fall 2025 Installment 2', amount: 1710.25 },
    { date: 'Dec 15, 2025', description: 'Fall 2025 Final Payment', amount: 1710.25 },
    { date: 'Jan 15, 2026', description: 'Spring 2026 Tuition', amount: 11220.00 }
  ];
  
  const bearcatDollars = {
    balance: 127.50,
    lastUsed: 'Yesterday at TUC Food Court',
    recentTransactions: [
      { date: 'Nov 5', location: 'TUC Food Court', amount: -8.50 },
      { date: 'Nov 4', location: 'Starbucks - Langsam', amount: -6.25 },
      { date: 'Nov 3', location: 'Campus Store', amount: -15.00 },
      { date: 'Nov 1', location: 'Added Funds', amount: 50.00 }
    ]
  };
  
  $: currentSemester = tuitionBreakdown[selectedSemester];
  
  function formatCurrency(amount) {
    return new Intl.NumberFormat('en-US', { 
      style: 'currency', 
      currency: 'USD' 
    }).format(amount);
  }
  
  function getStatusColor(status) {
    switch(status) {
      case 'Disbursed': return 'bg-green-100 text-green-700';
      case 'Pending': return 'bg-yellow-100 text-yellow-700';
      case 'In Progress': return 'bg-blue-100 text-blue-700';
      default: return 'bg-gray-100 text-gray-700';
    }
  }
</script>

<div class="max-w-7xl mx-auto space-y-6">
  <!--Account Summary-->
  <div class="bg-white border rounded-lg p-6">
    <h2 class="text-2xl font-semibold mb-6">Account Summary</h2>
    
    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
      <div class="p-4 bg-red-50 rounded-lg border border-red-200">
        <div class="text-sm text-gray-600 mb-1">Current Balance</div>
        <div class="text-3xl font-bold text-red-600">
          {formatCurrency(accountSummary.balance)}
        </div>
        <div class="text-xs text-gray-500 mt-2">Due: {accountSummary.dueDate}</div>
      </div>
      
      <div class="p-4 bg-blue-50 rounded-lg border border-blue-200">
        <div class="text-sm text-gray-600 mb-1">Next Payment</div>
        <div class="text-3xl font-bold text-blue-600">
          {formatCurrency(accountSummary.nextPayment)}
        </div>
        <div class="text-xs text-gray-500 mt-2">Due: {accountSummary.dueDate}</div>
      </div>
      
      <div class="p-4 bg-green-50 rounded-lg border border-green-200">
        <div class="text-sm text-gray-600 mb-1">Bearcat Dollars</div>
        <div class="text-3xl font-bold text-green-600">
          {formatCurrency(bearcatDollars.balance)}
        </div>
        <div class="text-xs text-gray-500 mt-2">Last: {bearcatDollars.lastUsed}</div>
      </div>
    </div>
    
    <div class="mt-6 flex gap-3">
      <button class="px-4 py-2 bg-red-600 text-white rounded hover:bg-red-700">
        Make a Payment
      </button>
      <button class="px-4 py-2 border rounded hover:bg-gray-50">
        Set Up Payment Plan
      </button>
      <button class="px-4 py-2 border rounded hover:bg-gray-50">
        Add Bearcat Dollars
      </button>
    </div>
  </div>
  
  <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
    <!----Tuition Breakdown -->
    <div class="bg-white border rounded-lg p-6">
      <div class="flex items-center justify-between mb-4">
        <h3 class="text-lg font-semibold">Tuition Breakdown</h3>
        <select 
          bind:value={selectedSemester}
          class="border rounded px-3 py-1 text-sm"
        >
          <option value="fall2025">Fall 2025</option>
          <option value="spring2025">Spring 2025</option>
        </select>
      </div>
      
      <div class="space-y-3">
        <div class="flex justify-between py-2 border-b">
          <span class="text-gray-600">Tuition</span>
          <span class="font-medium">{formatCurrency(currentSemester.tuition)}</span>
        </div>
        <div class="flex justify-between py-2 border-b">
          <span class="text-gray-600">Fees</span>
          <span class="font-medium">{formatCurrency(currentSemester.fees)}</span>
        </div>
        <div class="flex justify-between py-2 border-b">
          <span class="text-gray-600">Housing</span>
          <span class="font-medium">{formatCurrency(currentSemester.housing)}</span>
        </div>
        <div class="flex justify-between py-2 border-b">
          <span class="text-gray-600">Meal Plan</span>
          <span class="font-medium">{formatCurrency(currentSemester.mealPlan)}</span>
        </div>
        <div class="flex justify-between py-3 border-t-2 font-semibold text-lg">
          <span>Total</span>
          <span>{formatCurrency(currentSemester.total)}</span>
        </div>
        <div class="flex justify-between py-2 text-green-600">
          <span>Paid</span>
          <span>-{formatCurrency(currentSemester.paid)}</span>
        </div>
        <div class="flex justify-between py-3 border-t-2 font-bold text-lg text-red-600">
          <span>Remaining</span>
          <span>{formatCurrency(currentSemester.remaining)}</span>
        </div>
      </div>
      
      <!----Progress Bar -->
      <div class="mt-4">
        <div class="flex justify-between text-xs text-gray-600 mb-1">
          <span>Payment Progress</span>
          <span>{((currentSemester.paid / currentSemester.total) * 100).toFixed(0)}%</span>
        </div>
        <div class="w-full bg-gray-200 rounded-full h-2">
          <div 
            class="bg-green-600 h-2 rounded-full transition-all"
            style="width: {(currentSemester.paid / currentSemester.total) * 100}%"
          ></div>
        </div>
      </div>
    </div>
    
    <!----Financial Aid -->
    <div class="bg-white border rounded-lg p-6">
      <h3 class="text-lg font-semibold mb-4">Financial Aid</h3>
      
      <div class="space-y-3">
        {#each financialAid as aid}
          <div class="flex items-start justify-between p-3 bg-gray-50 rounded border">
            <div class="flex-1">
              <div class="font-medium text-sm">{aid.type}</div>
              <div class="text-xs text-gray-500 mt-1">{aid.date}</div>
            </div>
            <div class="text-right">
              <div class="font-semibold text-green-600">
                {formatCurrency(aid.amount)}
              </div>
              <span class="inline-block mt-1 px-2 py-1 text-xs rounded {getStatusColor(aid.status)}">
                {aid.status}
              </span>
            </div>
          </div>
        {/each}
      </div>
      
      <div class="mt-4 pt-4 border-t">
        <div class="flex justify-between font-semibold">
          <span>Total Aid</span>
          <span class="text-green-600">
            {formatCurrency(financialAid.reduce((sum, aid) => sum + aid.amount, 0))}
          </span>
        </div>
      </div>
      
      <button class="mt-4 w-full px-4 py-2 border rounded hover:bg-gray-50 text-sm">
        View Financial Aid Details
      </button>
    </div>
  </div>
  
  <!----Upcoming Payments -->
  <div class="bg-white border rounded-lg p-6">
    <h3 class="text-lg font-semibold mb-4">Upcoming Payments</h3>
    
    <div class="space-y-3">
      {#each upcomingPayments as payment}
        <div class="flex items-center justify-between p-3 border rounded hover:bg-gray-50">
          <div class="flex items-center gap-3">
            <div class="w-12 h-12 bg-red-100 rounded flex items-center justify-center text-red-600">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <div>
              <div class="font-medium">{payment.description}</div>
              <div class="text-sm text-gray-500">{payment.date}</div>
            </div>
          </div>
          <div class="text-right">
            <div class="font-semibold text-lg">{formatCurrency(payment.amount)}</div>
          </div>
        </div>
      {/each}
    </div>
  </div>
  
  <!----Payment History & Bearcat Dollars in 2 columns -->
  <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
    <!----Payment History -->
    <div class="lg:col-span-2 bg-white border rounded-lg p-6">
      <h3 class="text-lg font-semibold mb-4">Payment History</h3>
      
      <div class="overflow-x-auto">
        <table class="w-full text-sm">
          <thead class="border-b">
            <tr class="text-left text-gray-600">
              <th class="pb-3 font-medium">Date</th>
              <th class="pb-3 font-medium">Description</th>
              <th class="pb-3 font-medium text-right">Amount</th>
              <th class="pb-3 font-medium text-right">Balance</th>
            </tr>
          </thead>
          <tbody class="divide-y">
            {#each paymentHistory as transaction}
              <tr class="hover:bg-gray-50">
                <td class="py-3 text-gray-600">{transaction.date}</td>
                <td class="py-3">{transaction.description}</td>
                <td class="py-3 text-right font-medium {transaction.amount < 0 ? 'text-red-600' : 'text-green-600'}">
                  {formatCurrency(Math.abs(transaction.amount))}
                </td>
                <td class="py-3 text-right">{formatCurrency(transaction.balance)}</td>
              </tr>
            {/each}
          </tbody>
        </table>
      </div>
      
      <button class="mt-4 w-full px-4 py-2 border rounded hover:bg-gray-50 text-sm">
        View All Transactions
      </button>
    </div>
    
    <!----Bearcat Dollars Detail -->
    <div class="bg-white border rounded-lg p-6">
      <h3 class="text-lg font-semibold mb-4">Bearcat Dollars</h3>
      
      <div class="mb-4 p-4 bg-green-50 rounded border border-green-200 text-center">
        <div class="text-sm text-gray-600">Available Balance</div>
        <div class="text-3xl font-bold text-green-600 my-2">
          {formatCurrency(bearcatDollars.balance)}
        </div>
        <button class="mt-2 px-4 py-2 bg-green-600 text-white rounded hover:bg-green-700 text-sm w-full">
          Add Funds
        </button>
      </div>
      
      <h4 class="text-sm font-medium mb-2">Recent Transactions</h4>
      <div class="space-y-2">
        {#each bearcatDollars.recentTransactions as transaction}
          <div class="flex justify-between text-sm p-2 bg-gray-50 rounded">
            <div>
              <div class="font-medium text-xs">{transaction.location}</div>
              <div class="text-xs text-gray-500">{transaction.date}</div>
            </div>
            <div class="font-medium {transaction.amount < 0 ? 'text-red-600' : 'text-green-600'}">
              {transaction.amount < 0 ? '' : '+'}{formatCurrency(transaction.amount)}
            </div>
          </div>
        {/each}
      </div>
    </div>
  </div>
</div>