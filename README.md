
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kalipay - Tableau de Bord Admin</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
  <style>
    .nav-link { transition: all 0.2s ease; }
    .nav-link:hover { transform: translateX(4px); }
    .card-hover { transition: all 0.3s ease; }
    .card-hover:hover { transform: translateY(-4px); box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1); }
    .sidebar-active { background-color: #10b981; color: white; border-radius: 8px; }
    .content-section { display: none; }
    .content-section.active { display: block; }
  </style>
</head>
<body class="bg-gray-50 font-sans">
  <div class="flex h-screen overflow-hidden">
    <!-- Sidebar -->
    <div class="w-72 bg-white shadow-2xl flex flex-col">
      <div class="p-6 border-b">
        <div class="flex items-center gap-3">
          <div class="w-10 h-10 bg-emerald-600 rounded-2xl flex items-center justify-center text-white font-bold text-2xl">K</div>
          <div>
            <h1 class="text-3xl font-bold text-emerald-600">Kalipay</h1>
            <p class="text-xs text-gray-500">Administration</p>
          </div>
        </div>
      </div>
      <nav class="flex-1 p-4 space-y-1">
        <a href="#" onclick="navigateTo('dashboard'); return false;" class="nav-link flex items-center gap-3 px-4 py-3 text-gray-700 hover:bg-emerald-50 sidebar-active" id="nav-dashboard">
          <i class="fas fa-home w-5"></i><span class="font-medium">Tableau de bord</span>
        </a>
        <a href="#" onclick="navigateTo('users'); return false;" class="nav-link flex items-center gap-3 px-4 py-3 text-gray-700 hover:bg-emerald-50" id="nav-users">
          <i class="fas fa-users w-5"></i><span class="font-medium">Utilisateurs</span>
        </a>
        <a href="#" onclick="navigateTo('transactions'); return false;" class="nav-link flex items-center gap-3 px-4 py-3 text-gray-700 hover:bg-emerald-50" id="nav-transactions">
          <i class="fas fa-exchange-alt w-5"></i><span class="font-medium">Transactions</span>
        </a>
        <a href="#" onclick="navigateTo('services'); return false;" class="nav-link flex items-center gap-3 px-4 py-3 text-gray-700 hover:bg-emerald-50" id="nav-services">
          <i class="fas fa-cogs w-5"></i><span class="font-medium">Services</span>
        </a>
        <a href="#" onclick="navigateTo('reports'); return false;" class="nav-link flex items-center gap-3 px-4 py-3 text-gray-700 hover:bg-emerald-50" id="nav-reports">
          <i class="fas fa-chart-bar w-5"></i><span class="font-medium">Rapports</span>
        </a>
      </nav>
      <div class="p-4 border-t">
        <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-2xl">
          <div class="w-10 h-10 bg-emerald-100 rounded-xl flex items-center justify-center text-emerald-600">AU</div>
          <div class="flex-1"><p class="font-semibold text-sm">Admin User</p><p class="text-xs text-emerald-600">Super Admin</p></div>
          <button onclick="logout()" class="text-red-500 hover:text-red-600"><i class="fas fa-sign-out-alt"></i></button>
        </div>
      </div>
    </div>

    <!-- Main Content -->
    <div class="flex-1 flex flex-col">
      <header class="bg-white border-b px-8 py-5 flex justify-between items-center">
        <h2 class="text-2xl font-semibold text-gray-800" id="page-title">Tableau de bord</h2>
        <div class="flex items-center gap-6">
          <div class="relative">
            <input type="text" placeholder="Rechercher..." class="bg-gray-100 border border-gray-200 rounded-2xl pl-10 pr-4 py-2.5 w-72">
            <i class="fas fa-search absolute left-3.5 top-3 text-gray-400"></i>
          </div>
          <button class="relative p-2 hover:bg-gray-100 rounded-xl">
            <i class="fas fa-bell text-xl text-gray-600"></i>
            <span class="absolute top-1 right-1 w-4 h-4 bg-red-500 text-white text-[10px] flex items-center justify-center rounded-full">3</span>
          </button>
        </div>
      </header>
      
      <main class="flex-1 overflow-auto p-8">
        <!-- Dashboard -->
        <div id="content-dashboard" class="content-section active">
          <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6 mb-8">
            <div class="bg-white rounded-3xl p-6 card-hover">
              <div class="flex justify-between items-start">
                <div><p class="text-gray-500 text-sm">Total Utilisateurs</p><p class="text-4xl font-bold">12,543</p><p class="text-xs text-emerald-600 mt-2">↑ 12%</p></div>
                <i class="fas fa-users text-emerald-600 text-4xl opacity-20"></i>
              </div>
            </div>
            <div class="bg-white rounded-3xl p-6 card-hover">
              <div class="flex justify-between items-start">
                <div><p class="text-gray-500 text-sm">Transactions</p><p class="text-4xl font-bold">45,231</p><p class="text-xs text-emerald-600 mt-2">↑ 8%</p></div>
                <i class="fas fa-exchange-alt text-blue-600 text-4xl opacity-20"></i>
              </div>
            </div>
            <div class="bg-white rounded-3xl p-6 card-hover">
              <div class="flex justify-between items-start">
                <div><p class="text-gray-500 text-sm">Revenu Total</p><p class="text-4xl font-bold">$125K</p><p class="text-xs text-emerald-600 mt-2">↑ 23%</p></div>
                <i class="fas fa-dollar-sign text-yellow-600 text-4xl opacity-20"></i>
              </div>
            </div>
            <div class="bg-white rounded-3xl p-6 card-hover">
              <div class="flex justify-between items-start">
                <div><p class="text-gray-500 text-sm">Taux Succès</p><p class="text-4xl font-bold">99.2%</p><p class="text-xs text-emerald-600 mt-2">↑ 0.8%</p></div>
                <i class="fas fa-check-circle text-purple-600 text-4xl opacity-20"></i>
              </div>
            </div>
          </div>
          <div class="bg-white rounded-3xl p-6">
            <h3 class="font-semibold text-lg mb-6">Dernières Transactions</h3>
            <table class="w-full text-sm">
              <thead>
                <tr class="border-b text-left text-gray-500">
                  <th class="pb-3">Utilisateur</th><th class="pb-3">Montant</th><th class="pb-3">Service</th><th class="pb-3">Date</th><th class="pb-3">Statut</th>
                </tr>
              </thead>
              <tbody id="transactions-table"></tbody>
            </table>
          </div>
        </div>

        <!-- Users -->
        <div id="content-users" class="content-section">
          <div class="bg-white rounded-3xl p-6">
            <h3 class="font-semibold text-lg mb-6">Gestion Utilisateurs</h3>
            <table class="w-full text-sm">
              <thead>
                <tr class="border-b text-left text-gray-500">
                  <th class="pb-3">Nom</th><th class="pb-3">Email</th><th class="pb-3">Téléphone</th><th class="pb-3">Date</th><th class="pb-3">Statut</th><th class="pb-3">Actions</th>
                </tr>
              </thead>
              <tbody id="users-table"></tbody>
            </table>
          </div>
        </div>

        <!-- Transactions -->
        <div id="content-transactions" class="content-section">
          <div class="bg-white rounded-3xl p-6">
            <h3 class="font-semibold text-lg mb-6">Transactions Complètes</h3>
            <table class="w-full text-sm">
              <thead>
                <tr class="border-b text-left text-gray-500">
                  <th class="pb-3">ID</th><th class="pb-3">Utilisateur</th><th class="pb-3">Montant</th><th class="pb-3">Service</th><th class="pb-3">Date</th><th class="pb-3">Statut</th>
                </tr>
              </thead>
              <tbody id="all-transactions-table"></tbody>
            </table>
          </div>
        </div>

        <!-- Services -->
        <div id="content-services" class="content-section">
          <div class="bg-white rounded-3xl p-6">
            <h3 class="font-semibold text-lg mb-6">Services</h3>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6" id="services-grid"></div>
          </div>
        </div>

        <!-- Reports -->
        <div id="content-reports" class="content-section">
          <div class="bg-white rounded-3xl p-6">
            <h3 class="font-semibold text-lg mb-6">Rapports</h3>
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
              <div class="bg-gray-50 p-4 rounded-2xl h-64 flex items-center justify-center">
                <p class="text-gray-500">Graphique Transactions</p>
              </div>
              <div class="bg-gray-50 p-4 rounded-2xl">
                <p class="font-semibold mb-4">Répartition Services</p>
                <div class="space-y-3">
                  <div><div class="text-sm">Factures: 35%</div><div class="w-full h-2 bg-gray-200 rounded"><div class="h-full bg-emerald-600" style="width:35%"></div></div></div>
                  <div><div class="text-sm">Transferts: 40%</div><div class="w-full h-2 bg-gray-200 rounded"><div class="h-full bg-blue-600" style="width:40%"></div></div></div>
                  <div><div class="text-sm">Autres: 25%</div><div class="w-full h-2 bg-gray-200 rounded"><div class="h-full bg-purple-600" style="width:25%"></div></div></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </main>
    </div>
  </div>

  <script>
    const transactions = [
      {user:'Jean Dupont',amount:'$250',service:'Facture',date:'2024-01-15',status:'success'},
      {user:'Marie Laurent',amount:'$1,500',service:'Transfert',date:'2024-01-14',status:'success'},
      {user:'Pierre Bernard',amount:'$75',service:'Recharge',date:'2024-01-14',status:'pending'},
      {user:'Sophie Martin',amount:'$320',service:'Facture',date:'2024-01-13',status:'success'},
      {user:'Luc Rousseau',amount:'$2,100',service:'Transfert',date:'2024-01-13',status:'success'}
    ];
    const users = [
      {name:'Jean Dupont',email:'jean@example.com',phone:'+33612345678',date:'2023-06-15',status:'Actif'},
      {name:'Marie Laurent',email:'marie@example.com',phone:'+33623456789',date:'2023-07-20',status:'Actif'},
      {name:'Pierre Bernard',email:'pierre@example.com',phone:'+33634567890',date:'2023-08-10',status:'Inactif'},
      {name:'Sophie Martin',email:'sophie@example.com',phone:'+33645678901',date:'2023-09-05',status:'Actif'},
      {name:'Luc Rousseau',email:'luc@example.com',phone:'+33656789012',date:'2023-10-12',status:'Actif'}
    ];
    const services = [
      {name:'Paiement Factures',icon:'fa-file-invoice-dollar',color:'emerald'},
      {name:'Transfert Argent',icon:'fa-exchange-alt',color:'blue'},
      {name:'Recharge Mobile',icon:'fa-mobile-alt',color:'purple'}
    ];

    function loadTransactions(){
      document.getElementById('transactions-table').innerHTML=transactions.map(t=>`
        <tr class="border-b hover:bg-gray-50">
          <td class="py-4">${t.user}</td><td class="py-4 font-semibold">${t.amount}</td><td class="py-4">${t.service}</td><td class="py-4">${t.date}</td>
          <td class="py-4"><span class="px-3 py-1 rounded-full text-xs ${t.status==='success'?'bg-emerald-100 text-emerald-700':'bg-amber-100 text-amber-700'}">${t.status==='success'?'Succès':'En cours'}</span></td>
        </tr>`).join('');
    }
    function loadUsers(){
      document.getElementById('users-table').innerHTML=users.map(u=>`
        <tr class="border-b hover:bg-gray-50">
          <td class="py-4">${u.name}</td><td class="py-4">${u.email}</td><td class="py-4">${u.phone}</td><td class="py-4">${u.date}</td>
          <td class="py-4"><span class="px-3 py-1 rounded-full text-xs ${u.status==='Actif'?'bg-emerald-100 text-emerald-700':'bg-gray-100 text-gray-700'}">${u.status}</span></td>
          <td class="py-4"><button class="text-emerald-600 mr-2"><i class="fas fa-edit"></i></button><button class="text-red-600"><i class="fas fa-trash"></i></button></td>
        </tr>`).join('');
    }
    function loadAllTransactions(){
      document.getElementById('all-transactions-table').innerHTML=transactions.map((t,i)=>`
        <tr class="border-b hover:bg-gray-50">
          <td class="py-4">#TXN${String(1000+i).slice(-4)}</td><td class="py-4">${t.user}</td><td class="py-4 font-semibold">${t.amount}</td><td class="py-4">${t.service}</td><td class="py-4">${t.date}</td>
          <td class="py-4"><span class="px-3 py-1 rounded-full text-xs ${t.status==='success'?'bg-emerald-100 text-emerald-700':'bg-amber-100 text-amber-700'}">${t.status==='success'?'Succès':'En cours'}</span></td>
        </tr>`).join('');
    }
    function loadServices(){
      document.getElementById('services-grid').innerHTML=services.map(s=>`
        <div class="bg-gray-50 rounded-2xl p-6 text-center hover:shadow-lg transition">
          <i class="fas ${s.icon} text-${s.color}-600 text-4xl mb-4 block"></i>
          <h4 class="font-semibold mb-2">${s.name}</h4><p class="text-sm text-gray-600 mb-4">Actif</p>
          <button class="text-emerald-600 text-sm hover:underline">Gérer →</button>
        </div>`).join('');
    }
    function navigateTo(page){
      document.querySelectorAll('.content-section').forEach(s=>s.classList.remove('active'));
      document.getElementById(`content-${page}`).classList.add('active');
      const titles={'dashboard':'Tableau de bord','users':'Utilisateurs','transactions':'Transactions','services':'Services','reports':'Rapports'};
      document.getElementById('page-title').textContent=titles[page];
      document.querySelectorAll('.nav-link').forEach(l=>l.classList.remove('sidebar-active'));
      document.getElementById(`nav-${page}`).classList.add('sidebar-active');
      if(page==='dashboard')loadTransactions();else if(page==='users')loadUsers();else if(page==='transactions')loadAllTransactions();else if(page==='services')loadServices();
    }
    function logout(){alert('Déconnexion...');}
    document.addEventListener('DOMContentLoaded',()=>{loadTransactions();loadServices();});
  </script>
</body>
</html>
