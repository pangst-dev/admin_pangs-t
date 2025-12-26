<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PANGS!T - Admin Dashboard</title>
    
    <!-- Favicon -->
    <link rel="icon" href="foto/logo projek.png" type="image/png">
    
    <!-- Font Awesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* Reset dan variabel CSS */
        :root {
            --primary: #ff6b35;
            --primary-dark: #e55a2b;
            --secondary: #2d3047;
            --light: #f8f9fa;
            --dark: #212529;
            --gray: #6c757d;
            --light-gray: #e9ecef;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
            --info: #17a2b8;
            --sidebar-width: 250px;
            --header-height: 70px;
            --shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            --transition: all 0.3s ease;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: var(--dark);
            line-height: 1.6;
        }
        
        /* Layout Utama */
        .admin-container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar */
        .sidebar {
            width: var(--sidebar-width);
            background-color: var(--secondary);
            color: white;
            position: fixed;
            height: 100vh;
            overflow-y: auto;
            transition: var(--transition);
            z-index: 100;
        }
        
        .sidebar-header {
            padding: 25px 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .sidebar-logo {
            font-size: 24px;
            font-weight: 700;
            color: white;
        }
        
        .sidebar-logo span {
            color: var(--primary);
        }
        
        .sidebar-menu {
            padding: 20px 0;
        }
        
        .menu-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 15px 20px;
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            transition: var(--transition);
            border-left: 4px solid transparent;
        }
        
        .menu-item:hover, .menu-item.active {
            background-color: rgba(255, 255, 255, 0.1);
            color: white;
            border-left-color: var(--primary);
        }
        
        .menu-item i {
            width: 24px;
            text-align: center;
        }
        
        .menu-item.active {
            font-weight: 600;
        }
        
        /* Main Content */
        .main-content {
            flex: 1;
            margin-left: var(--sidebar-width);
            transition: var(--transition);
        }
        
        /* Header */
        .header {
            height: var(--header-height);
            background-color: white;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 30px;
            position: sticky;
            top: 0;
            z-index: 99;
        }
        
        .header-left h1 {
            font-size: 24px;
            color: var(--secondary);
        }
        
        .header-right {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        
        .admin-info {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .admin-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background-color: var(--primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }
        
        .logout-btn {
            background-color: var(--danger);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 600;
        }
        
        .logout-btn:hover {
            background-color: #c82333;
        }
        
        /* Content Area */
        .content {
            padding: 30px;
        }
        
        /* Dashboard Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 20px;
            transition: var(--transition);
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
        }
        
        .stat-icon {
            width: 60px;
            height: 60px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
        }
        
        .stat-1 .stat-icon {
            background-color: rgba(255, 107, 53, 0.1);
            color: var(--primary);
        }
        
        .stat-2 .stat-icon {
            background-color: rgba(40, 167, 69, 0.1);
            color: var(--success);
        }
        
        .stat-3 .stat-icon {
            background-color: rgba(23, 162, 184, 0.1);
            color: var(--info);
        }
        
        .stat-4 .stat-icon {
            background-color: rgba(255, 193, 7, 0.1);
            color: var(--warning);
        }
        
        .stat-info h3 {
            font-size: 28px;
            margin-bottom: 5px;
        }
        
        .stat-info p {
            color: var(--gray);
            font-size: 14px;
        }
        
        /* Cards Umum */
        .card {
            background-color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
            overflow: hidden;
        }
        
        .card-header {
            padding: 20px 25px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .card-header h2 {
            color: var(--secondary);
            font-size: 20px;
        }
        
        .card-body {
            padding: 25px;
        }
        
        /* Tabel */
        .table-responsive {
            overflow-x: auto;
        }
        
        .data-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .data-table th {
            background-color: var(--light-gray);
            padding: 15px;
            text-align: left;
            color: var(--secondary);
            font-weight: 600;
            white-space: nowrap;
        }
        
        .data-table td {
            padding: 15px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .data-table tr:hover {
            background-color: rgba(0, 0, 0, 0.02);
        }
        
        /* Status Badge */
        .status-badge {
            display: inline-block;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .status-pending {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .status-paid {
            background-color: #cce5ff;
            color: #004085;
        }
        
        .status-processing {
            background-color: #d1ecf1;
            color: #0c5460;
        }
        
        .status-shipped {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status-delivered {
            background-color: #d1e7dd;
            color: #0f5132;
        }
        
        .status-cancelled {
            background-color: #f8d7da;
            color: #721c24;
        }
        
        /* Action Buttons */
        .action-buttons {
            display: flex;
            gap: 5px;
        }
        
        .btn-action {
            width: 35px;
            height: 35px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .btn-view {
            background-color: #e7f4ff;
            color: #0066cc;
        }
        
        .btn-edit {
            background-color: #fff8e1;
            color: #ff9800;
        }
        
        .btn-delete {
            background-color: #fdecea;
            color: #f44336;
        }
        
        .btn-status {
            background-color: #e8f5e9;
            color: #4caf50;
        }
        
        .btn-action:hover {
            opacity: 0.8;
        }
        
        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 1100;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .modal.active {
            display: flex;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 10px;
            max-width: 800px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
        }
        
        .modal-header {
            padding: 20px 25px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .modal-header h3 {
            color: var(--secondary);
            font-size: 22px;
        }
        
        .close-modal {
            background: none;
            border: none;
            font-size: 24px;
            color: var(--gray);
            cursor: pointer;
        }
        
        .modal-body {
            padding: 25px;
        }
        
        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary);
        }
        
        .form-control {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            font-size: 16px;
            transition: var(--transition);
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        .form-row {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }
        
        /* Button Styles */
        .btn {
            display: inline-block;
            background-color: var(--primary);
            color: white;
            padding: 12px 24px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 600;
            font-size: 14px;
            border: none;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .btn:hover {
            background-color: var(--primary-dark);
        }
        
        .btn-secondary {
            background-color: var(--secondary);
        }
        
        .btn-secondary:hover {
            background-color: #1f2135;
        }
        
        .btn-success {
            background-color: var(--success);
        }
        
        .btn-success:hover {
            background-color: #218838;
        }
        
        /* Order Details */
        .order-details-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .detail-section {
            background-color: #f8f9fa;
            padding: 20px;
            border-radius: 8px;
        }
        
        .detail-section h4 {
            color: var(--secondary);
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid #dee2e6;
        }
        
        .detail-item {
            display: flex;
            margin-bottom: 10px;
        }
        
        .detail-label {
            font-weight: 600;
            width: 140px;
            color: var(--secondary);
        }
        
        /* Product Management */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 20px;
        }
        
        .product-admin-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid var(--light-gray);
        }
        
        .product-admin-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        }
        
        .product-admin-img {
            height: 180px;
            width: 100%;
            object-fit: cover;
        }
        
        .product-admin-info {
            padding: 20px;
        }
        
        .product-admin-name {
            font-size: 18px;
            margin-bottom: 10px;
            color: var(--secondary);
        }
        
        .product-admin-price {
            font-size: 20px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .product-admin-category {
            display: inline-block;
            padding: 4px 10px;
            background-color: var(--light-gray);
            color: var(--gray);
            border-radius: 20px;
            font-size: 12px;
            margin-bottom: 15px;
        }
        
        /* Search and Filter */
        .search-filter {
            display: flex;
            gap: 15px;
            margin-bottom: 20px;
            flex-wrap: wrap;
        }
        
        .search-box {
            flex: 1;
            min-width: 250px;
        }
        
        .filter-box {
            width: 200px;
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            .sidebar {
                transform: translateX(-100%);
            }
            
            .sidebar.active {
                transform: translateX(0);
            }
            
            .main-content {
                margin-left: 0;
            }
            
            .header {
                padding: 0 20px;
            }
            
            .menu-toggle {
                display: block;
            }
        }
        
        @media (max-width: 768px) {
            .content {
                padding: 20px;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .header-left h1 {
                font-size: 20px;
            }
            
            .search-filter {
                flex-direction: column;
            }
            
            .search-box, .filter-box {
                width: 100%;
            }
        }
        
        /* Menu Toggle Button */
        .menu-toggle {
            display: none;
            background: none;
            border: none;
            font-size: 24px;
            color: var(--secondary);
            cursor: pointer;
            margin-right: 15px;
        }
        
        @media (max-width: 992px) {
            .menu-toggle {
                display: block;
            }
        }
        
        /* Login Page */
        .login-container {
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            padding: 20px;
        }
        
        .login-box {
            background-color: white;
            border-radius: 15px;
            padding: 40px;
            width: 100%;
            max-width: 400px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
        }
        
        .login-logo {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .login-logo h1 {
            font-size: 32px;
            color: var(--secondary);
        }
        
        .login-logo span {
            color: var(--primary);
        }
        
        .login-form .form-group {
            margin-bottom: 25px;
        }
        
        .login-btn {
            width: 100%;
            padding: 14px;
            font-size: 16px;
            margin-top: 10px;
        }
        
        /* Export Button */
        .export-btn {
            background-color: var(--success);
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
        }
        
        .export-btn:hover {
            background-color: #218838;
        }
        
        /* Empty State */
        .empty-state {
            text-align: center;
            padding: 40px;
            color: var(--gray);
        }
        
        .empty-state i {
            font-size: 60px;
            margin-bottom: 20px;
            color: var(--light-gray);
        }
        
        /* Date Range Picker */
        .date-range {
            display: flex;
            align-items: center;
            gap: 10px;
            flex-wrap: wrap;
        }
    </style>
</head>
<body>
    <!-- Admin Login Page -->
    <div id="loginPage" class="login-container">
        <div class="login-box">
            <div class="login-logo">
                <h1>PANGS!T <span>Admin</span></h1>
                <p style="color: var(--gray); margin-top: 10px;">Masuk ke Dashboard Admin</p>
            </div>
            
            <form id="loginForm">
                <div class="form-group">
                    <label for="adminUsername">Username</label>
                    <input type="text" id="adminUsername" class="form-control" placeholder="Masukkan username" required>
                </div>
                
                <div class="form-group">
                    <label for="adminPassword">Password</label>
                    <input type="password" id="adminPassword" class="form-control" placeholder="Masukkan password" required>
                </div>
                
                <button type="submit" class="btn login-btn">Masuk</button>
                
                <div style="text-align: center; margin-top: 20px; color: var(--gray); font-size: 14px;">
                    <p>Default login: admin / admin123</p>
                </div>
            </form>
        </div>
    </div>
    
    <!-- Admin Dashboard (hidden by default) -->
    <div id="adminDashboard" class="admin-container" style="display: none;">
        <!-- Sidebar -->
        <div class="sidebar" id="sidebar">
            <div class="sidebar-header">
                <h1 class="sidebar-logo">PANGS!T <span>Admin</span></h1>
            </div>
            
            <div class="sidebar-menu">
                <a href="#" class="menu-item active" data-page="dashboard">
                    <i class="fas fa-tachometer-alt"></i>
                    <span>Dashboard</span>
                </a>
                
                <a href="#" class="menu-item" data-page="orders">
                    <i class="fas fa-shopping-bag"></i>
                    <span>Pesanan</span>
                </a>
                
                <a href="#" class="menu-item" data-page="products">
                    <i class="fas fa-dumpling"></i>
                    <span>Produk</span>
                </a>
                
                <a href="#" class="menu-item" data-page="reports">
                    <i class="fas fa-chart-bar"></i>
                    <span>Laporan</span>
                </a>
                
                <a href="#" class="menu-item" data-page="customers">
                    <i class="fas fa-users"></i>
                    <span>Pelanggan</span>
                </a>
            </div>
            
            <div style="padding: 20px; position: absolute; bottom: 20px; width: 100%;">
                <div style="background-color: rgba(255, 255, 255, 0.1); padding: 15px; border-radius: 8px;">
                    <div style="display: flex; align-items: center; gap: 10px; margin-bottom: 10px;">
                        <div class="admin-avatar" id="adminAvatar">A</div>
                        <div>
                            <div style="font-weight: 600;" id="adminName">Administrator</div>
                            <div style="font-size: 12px; opacity: 0.8;">Admin Panel</div>
                        </div>
                    </div>
                    <button class="logout-btn" id="logoutBtn" style="width: 100%;">
                        <i class="fas fa-sign-out-alt"></i> Logout
                    </button>
                </div>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <!-- Header -->
            <div class="header">
                <div style="display: flex; align-items: center;">
                    <button class="menu-toggle" id="menuToggle">
                        <i class="fas fa-bars"></i>
                    </button>
                    <div class="header-left">
                        <h1 id="pageTitle">Dashboard</h1>
                    </div>
                </div>
                
                <div class="header-right">
                    <div class="admin-info">
                        <div class="admin-avatar" id="headerAdminAvatar">A</div>
                        <div>
                            <div style="font-weight: 600;" id="headerAdminName">Admin</div>
                            <div style="font-size: 12px; color: var(--gray);" id="currentDate"></div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Content Area -->
            <div class="content" id="contentArea">
                <!-- Dashboard Page -->
                <div id="dashboardPage" class="page-content">
                    <!-- Stats -->
                    <div class="stats-grid">
                        <div class="stat-card stat-1">
                            <div class="stat-icon">
                                <i class="fas fa-shopping-bag"></i>
                            </div>
                            <div class="stat-info">
                                <h3 id="totalOrders">0</h3>
                                <p>Total Pesanan</p>
                            </div>
                        </div>
                        
                        <div class="stat-card stat-2">
                            <div class="stat-icon">
                                <i class="fas fa-money-bill-wave"></i>
                            </div>
                            <div class="stat-info">
                                <h3 id="totalRevenue">Rp 0</h3>
                                <p>Pendapatan Hari Ini</p>
                            </div>
                        </div>
                        
                        <div class="stat-card stat-3">
                            <div class="stat-icon">
                                <i class="fas fa-users"></i>
                            </div>
                            <div class="stat-info">
                                <h3 id="totalCustomers">0</h3>
                                <p>Total Pelanggan</p>
                            </div>
                        </div>
                        
                        <div class="stat-card stat-4">
                            <div class="stat-icon">
                                <i class="fas fa-dumpling"></i>
                            </div>
                            <div class="stat-info">
                                <h3 id="totalProducts">0</h3>
                                <p>Total Produk</p>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Recent Orders -->
                    <div class="card">
                        <div class="card-header">
                            <h2>Pesanan Terbaru</h2>
                            <a href="#" class="btn btn-secondary" data-page="orders">Lihat Semua</a>
                        </div>
                        <div class="card-body">
                            <div class="table-responsive">
                                <table class="data-table">
                                    <thead>
                                        <tr>
                                            <th>Order ID</th>
                                            <th>Pelanggan</th>
                                            <th>Tanggal</th>
                                            <th>Total</th>
                                            <th>Status</th>
                                            <th>Aksi</th>
                                        </tr>
                                    </thead>
                                    <tbody id="recentOrdersTable">
                                        <!-- Recent orders will be loaded here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Sales Chart -->
                    <div class="card">
                        <div class="card-header">
                            <h2>Penjualan 7 Hari Terakhir</h2>
                        </div>
                        <div class="card-body">
                            <div style="height: 300px; display: flex; align-items: center; justify-content: center; background-color: #f8f9fa; border-radius: 8px;">
                                <canvas id="salesChart"></canvas>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Orders Page -->
                <div id="ordersPage" class="page-content" style="display: none;">
                    <div class="card">
                        <div class="card-header">
                            <h2>Kelola Pesanan</h2>
                            <div style="display: flex; gap: 10px;">
                                <button class="export-btn" id="exportOrdersBtn">
                                    <i class="fas fa-download"></i> Export
                                </button>
                            </div>
                        </div>
                        <div class="card-body">
                            <!-- Filter and Search -->
                            <div class="search-filter">
                                <div class="search-box">
                                    <input type="text" id="orderSearch" class="form-control" placeholder="Cari Order ID atau nama pelanggan...">
                                </div>
                                <div class="filter-box">
                                    <select id="statusFilter" class="form-control">
                                        <option value="">Semua Status</option>
                                        <option value="paid">Lunas</option>
                                        <option value="processing">Diproses</option>
                                        <option value="shipped">Dikirim</option>
                                        <option value="delivered">Selesai</option>
                                        <option value="cancelled">Dibatalkan</option>
                                    </select>
                                </div>
                                <div class="filter-box">
                                    <input type="date" id="dateFilter" class="form-control">
                                </div>
                            </div>
                            
                            <!-- Orders Table -->
                            <div class="table-responsive">
                                <table class="data-table">
                                    <thead>
                                        <tr>
                                            <th>Order ID</th>
                                            <th>Pelanggan</th>
                                            <th>Tanggal</th>
                                            <th>Items</th>
                                            <th>Total</th>
                                            <th>Status</th>
                                            <th>Aksi</th>
                                        </tr>
                                    </thead>
                                    <tbody id="ordersTable">
                                        <!-- Orders will be loaded here -->
                                    </tbody>
                                </table>
                            </div>
                            
                            <!-- Pagination -->
                            <div style="display: flex; justify-content: space-between; align-items: center; margin-top: 20px;">
                                <div id="ordersPaginationInfo" style="color: var(--gray);">
                                    Menampilkan 0 dari 0 pesanan
                                </div>
                                <div style="display: flex; gap: 5px;">
                                    <button class="btn btn-secondary" id="prevPageBtn" disabled>
                                        <i class="fas fa-chevron-left"></i>
                                    </button>
                                    <button class="btn btn-secondary" id="nextPageBtn" disabled>
                                        <i class="fas fa-chevron-right"></i>
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Products Page -->
                <div id="productsPage" class="page-content" style="display: none;">
                    <div class="card">
                        <div class="card-header">
                            <h2>Kelola Produk</h2>
                            <button class="btn" id="addProductBtn">
                                <i class="fas fa-plus"></i> Tambah Produk
                            </button>
                        </div>
                        <div class="card-body">
                            <!-- Search -->
                            <div class="search-filter">
                                <div class="search-box">
                                    <input type="text" id="productSearch" class="form-control" placeholder="Cari produk...">
                                </div>
                            </div>
                            
                            <!-- Products Grid -->
                            <div class="products-grid" id="productsGridAdmin">
                                <!-- Products will be loaded here -->
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Reports Page -->
                <div id="reportsPage" class="page-content" style="display: none;">
                    <div class="card">
                        <div class="card-header">
                            <h2>Laporan Penjualan</h2>
                            <div style="display: flex; gap: 10px;">
                                <button class="export-btn" id="exportReportBtn">
                                    <i class="fas fa-download"></i> Export Laporan
                                </button>
                            </div>
                        </div>
                        <div class="card-body">
                            <!-- Date Range Filter -->
                            <div class="search-filter">
                                <div class="date-range">
                                    <div>
                                        <label>Dari Tanggal</label>
                                        <input type="date" id="reportDateFrom" class="form-control">
                                    </div>
                                    <div>
                                        <label>Sampai Tanggal</label>
                                        <input type="date" id="reportDateTo" class="form-control">
                                    </div>
                                    <div>
                                        <label>&nbsp;</label>
                                        <button class="btn" id="filterReportBtn">Filter</button>
                                    </div>
                                    <div>
                                        <label>&nbsp;</label>
                                        <button class="btn btn-secondary" id="resetReportBtn">Reset</button>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Report Summary -->
                            <div class="stats-grid" style="margin-bottom: 30px;">
                                <div class="stat-card stat-1">
                                    <div class="stat-icon">
                                        <i class="fas fa-shopping-bag"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3 id="reportTotalOrders">0</h3>
                                        <p>Total Pesanan</p>
                                    </div>
                                </div>
                                
                                <div class="stat-card stat-2">
                                    <div class="stat-icon">
                                        <i class="fas fa-money-bill-wave"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3 id="reportTotalRevenue">Rp 0</h3>
                                        <p>Total Pendapatan</p>
                                    </div>
                                </div>
                                
                                <div class="stat-card stat-3">
                                    <div class="stat-icon">
                                        <i class="fas fa-box"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3 id="reportTotalItems">0</h3>
                                        <p>Total Item Terjual</p>
                                    </div>
                                </div>
                                
                                <div class="stat-card stat-4">
                                    <div class="stat-icon">
                                        <i class="fas fa-user-check"></i>
                                    </div>
                                    <div class="stat-info">
                                        <h3 id="reportTotalCustomers">0</h3>
                                        <p>Pelanggan Baru</p>
                                    </div>
                                </div>
                            </div>
                            
                            <!-- Sales Table -->
                            <div class="table-responsive">
                                <table class="data-table">
                                    <thead>
                                        <tr>
                                            <th>Tanggal</th>
                                            <th>Order ID</th>
                                            <th>Pelanggan</th>
                                            <th>Items</th>
                                            <th>Total</th>
                                            <th>Status</th>
                                        </tr>
                                    </thead>
                                    <tbody id="reportTable">
                                        <!-- Report data will be loaded here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
                
                <!-- Customers Page -->
                <div id="customersPage" class="page-content" style="display: none;">
                    <div class="card">
                        <div class="card-header">
                            <h2>Data Pelanggan</h2>
                        </div>
                        <div class="card-body">
                            <!-- Search -->
                            <div class="search-filter">
                                <div class="search-box">
                                    <input type="text" id="customerSearch" class="form-control" placeholder="Cari pelanggan...">
                                </div>
                            </div>
                            
                            <!-- Customers Table -->
                            <div class="table-responsive">
                                <table class="data-table">
                                    <thead>
                                        <tr>
                                            <th>Nama</th>
                                            <th>Email</th>
                                            <th>Telepon</th>
                                            <th>Total Pesanan</th>
                                            <th>Total Belanja</th>
                                            <th>Pesanan Terakhir</th>
                                        </tr>
                                    </thead>
                                    <tbody id="customersTable">
                                        <!-- Customers will be loaded here -->
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Order Detail Modal -->
    <div class="modal" id="orderDetailModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Detail Pesanan</h3>
                <button class="close-modal" id="closeOrderModal">&times;</button>
            </div>
            <div class="modal-body" id="orderDetailContent">
                <!-- Order details will be loaded here -->
            </div>
        </div>
    </div>
    
    <!-- Product Modal (Add/Edit) -->
    <div class="modal" id="productModal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="productModalTitle">Tambah Produk Baru</h3>
                <button class="close-modal" id="closeProductModal">&times;</button>
            </div>
            <div class="modal-body">
                <form id="productForm">
                    <input type="hidden" id="productId">
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="productName">Nama Produk *</label>
                            <input type="text" id="productName" class="form-control" required>
                        </div>
                        
                        <div class="form-group">
                            <label for="productPrice">Harga (Rp) *</label>
                            <input type="number" id="productPrice" class="form-control" required min="1000">
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="productCategory">Kategori *</label>
                            <select id="productCategory" class="form-control" required>
                                <option value="">Pilih Kategori</option>
                                <option value="pedas">Pedas</option>
                                <option value="original">Original</option>
                                <option value="ayam">Ayam</option>
                                <option value="udang">Udang</option>
                                <option value="special">Special</option>
                            </select>
                        </div>
                        
                        <div class="form-group">
                            <label for="productStock">Stok *</label>
                            <input type="number" id="productStock" class="form-control" required min="0" value="10">
                        </div>
                    </div>
                    
                    <div class="form-group">
                        <label for="productDescription">Deskripsi *</label>
                        <textarea id="productDescription" class="form-control" rows="3" required></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="productDetails">Detail Produk</label>
                        <textarea id="productDetails" class="form-control" rows="3"></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="productImage">URL Gambar</label>
                        <input type="text" id="productImage" class="form-control" placeholder="https://example.com/image.jpg">
                        <small style="color: var(--gray);">Kosongkan untuk menggunakan gambar default</small>
                    </div>
                    
                    <div style="display: flex; gap: 10px; margin-top: 20px;">
                        <button type="button" class="btn btn-secondary" id="cancelProductBtn">Batal</button>
                        <button type="submit" class="btn" id="saveProductBtn">Simpan Produk</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
    
    <!-- Confirm Modal -->
    <div class="modal" id="confirmModal">
        <div class="modal-content" style="max-width: 500px;">
            <div class="modal-header">
                <h3 id="confirmModalTitle">Konfirmasi</h3>
                <button class="close-modal" id="closeConfirmModal">&times;</button>
            </div>
            <div class="modal-body">
                <p id="confirmModalMessage">Apakah Anda yakin?</p>
                <div style="display: flex; gap: 10px; margin-top: 20px;">
                    <button class="btn btn-secondary" id="cancelConfirmBtn">Batal</button>
                    <button class="btn btn-danger" id="confirmActionBtn">Ya, Lanjutkan</button>
                </div>
            </div>
        </div>
    </div>

    <!-- Chart.js Library -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

    <script>
        // ==================== DATA & STATE ====================
        let allOrders = JSON.parse(localStorage.getItem('customerOrders')) || [];
        let allProducts = JSON.parse(localStorage.getItem('adminProducts')) || [];
        let adminData = JSON.parse(localStorage.getItem('adminData')) || {
            username: 'admin',
            password: 'admin123',
            name: 'Administrator'
        };
        
        let currentAdmin = null;
        let currentPage = 'dashboard';
        let currentOrderPage = 1;
        let ordersPerPage = 10;
        
        // Default products if none exist
        if (allProducts.length === 0) {
            allProducts = [
                {
                    id: 1,
                    name: "fire silk wonton",
                    price: 20000,
                    image: "foto/fire silk wonton.jpg",
                    description: "Kesan: lembut, pedas aromatik, classy dengan minyak cabai khas Asia.",
                    details: "Kesan: lembut, pedas aromatik, classy dengan minyak cabai khas Asia.",
                    category: "pedas",
                    stock: 50
                },
                {
                    id: 2,
                    name: "crispy melt deluxe",
                    price: 13000,
                    image: "foto/crispy melt deluxe.jpg",
                    description: "Kesan: garing di luar, lembut & creamy di dalam.",
                    details: "Kesan: garing di luar, lembut & creamy di dalam.",
                    category: "original",
                    stock: 40
                },
                {
                    id: 3,
                    name: "Golden chili crunch",
                    price: 15000,
                    image: "foto/Golden chili crunch.jpg",
                    description: "Kesan: renyah, gurih dengan sentuhan manis-pedas saus khas.",
                    details: "Kesan: renyah, gurih dengan sentuhan manis-pedas saus khas.",
                    category: "pedas",
                    stock: 35
                },
                {
                    id: 4,
                    name: "bila bila ayam pangsit",
                    price: 10000,
                    image: "foto/bils bila ayam pangsit.jpg",
                    description: "Isi ayam lembut dengan bumbu bawang, merica, dan sedikit sayuran—rasa gurih klasik.",
                    details: "Isi ayam lembut dengan bumbu bawang, merica, dan sedikit sayuran—rasa gurih klasik.",
                    category: "ayam",
                    stock: 60
                },
                {
                    id: 5,
                    name: "pangsit kuah mercon",
                    price: 20000,
                    image: "foto/pangsit kuah mercon.jpg",
                    description: "Cocok untuk pangsit kuah. Menggunakan cabai rawit, sambal mercon, dan bumbu pedas gurih.",
                    details: "Cocok untuk pangsit kuah. Menggunakan cabai rawit, sambal mercon, dan bumbu pedas gurih.",
                    category: "pedas",
                    stock: 45
                },
                {
                    id: 6,
                    name: "pangsit isi tahu",
                    price: 15000,
                    image: "foto/pangsit isi tahu.jpg",
                    description: "Pangsit goreng dengan isian udang utuh yang segar.",
                    details: "Setiap pangsit berisi udang utuh pilihan dengan bumbu spesial. Sangat cocok untuk pecinta seafood.",
                    category: "udang",
                    stock: 30
                }
            ];
            localStorage.setItem('adminProducts', JSON.stringify(allProducts));
        }
        
        // ==================== DOM ELEMENTS ====================
        const loginPage = document.getElementById('loginPage');
        const adminDashboard = document.getElementById('adminDashboard');
        const loginForm = document.getElementById('loginForm');
        const logoutBtn = document.getElementById('logoutBtn');
        const menuToggle = document.getElementById('menuToggle');
        const sidebar = document.getElementById('sidebar');
        const contentArea = document.getElementById('contentArea');
        const pageTitle = document.getElementById('pageTitle');
        
        // Pages
        const dashboardPage = document.getElementById('dashboardPage');
        const ordersPage = document.getElementById('ordersPage');
        const productsPage = document.getElementById('productsPage');
        const reportsPage = document.getElementById('reportsPage');
        const customersPage = document.getElementById('customersPage');
        
        // Dashboard Elements
        const totalOrders = document.getElementById('totalOrders');
        const totalRevenue = document.getElementById('totalRevenue');
        const totalCustomers = document.getElementById('totalCustomers');
        const totalProducts = document.getElementById('totalProducts');
        const recentOrdersTable = document.getElementById('recentOrdersTable');
        
        // Orders Elements
        const ordersTable = document.getElementById('ordersTable');
        const orderSearch = document.getElementById('orderSearch');
        const statusFilter = document.getElementById('statusFilter');
        const dateFilter = document.getElementById('dateFilter');
        const exportOrdersBtn = document.getElementById('exportOrdersBtn');
        const prevPageBtn = document.getElementById('prevPageBtn');
        const nextPageBtn = document.getElementById('nextPageBtn');
        const ordersPaginationInfo = document.getElementById('ordersPaginationInfo');
        
        // Products Elements
        const productsGridAdmin = document.getElementById('productsGridAdmin');
        const productSearch = document.getElementById('productSearch');
        const addProductBtn = document.getElementById('addProductBtn');
        
        // Reports Elements
        const reportDateFrom = document.getElementById('reportDateFrom');
        const reportDateTo = document.getElementById('reportDateTo');
        const filterReportBtn = document.getElementById('filterReportBtn');
        const resetReportBtn = document.getElementById('resetReportBtn');
        const exportReportBtn = document.getElementById('exportReportBtn');
        const reportTotalOrders = document.getElementById('reportTotalOrders');
        const reportTotalRevenue = document.getElementById('reportTotalRevenue');
        const reportTotalItems = document.getElementById('reportTotalItems');
        const reportTotalCustomers = document.getElementById('reportTotalCustomers');
        const reportTable = document.getElementById('reportTable');
        
        // Customers Elements
        const customersTable = document.getElementById('customersTable');
        const customerSearch = document.getElementById('customerSearch');
        
        // Modals
        const orderDetailModal = document.getElementById('orderDetailModal');
        const orderDetailContent = document.getElementById('orderDetailContent');
        const closeOrderModal = document.getElementById('closeOrderModal');
        
        const productModal = document.getElementById('productModal');
        const productModalTitle = document.getElementById('productModalTitle');
        const productForm = document.getElementById('productForm');
        const closeProductModal = document.getElementById('closeProductModal');
        const cancelProductBtn = document.getElementById('cancelProductBtn');
        const saveProductBtn = document.getElementById('saveProductBtn');
        
        const confirmModal = document.getElementById('confirmModal');
        const confirmModalTitle = document.getElementById('confirmModalTitle');
        const confirmModalMessage = document.getElementById('confirmModalMessage');
        const closeConfirmModal = document.getElementById('closeConfirmModal');
        const cancelConfirmBtn = document.getElementById('cancelConfirmBtn');
        const confirmActionBtn = document.getElementById('confirmActionBtn');
        
        // Chart
        let salesChart = null;
        
        // ==================== UTILITY FUNCTIONS ====================
        function formatRupiah(amount) {
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(amount);
        }
        
        function formatDate(dateString) {
            if (!dateString) return '-';
            const date = new Date(dateString);
            return date.toLocaleDateString('id-ID', {
                day: '2-digit',
                month: 'short',
                year: 'numeric'
            });
        }
        
        function getStatusText(status) {
            const statusMap = {
                'paid': 'Lunas',
                'processing': 'Diproses',
                'shipped': 'Dikirim',
                'delivered': 'Selesai',
                'cancelled': 'Dibatalkan'
            };
            return statusMap[status] || status;
        }
        
        function getStatusClass(status) {
            return `status-${status}`;
        }
        
        function showNotification(message, type = 'success') {
            // Hapus notifikasi sebelumnya jika ada
            const existingNotification = document.querySelector('.notification');
            if (existingNotification) {
                existingNotification.remove();
            }
            
            // Buat elemen notifikasi
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.textContent = message;
            notification.style.cssText = `
                position: fixed;
                top: 100px;
                right: 20px;
                background-color: ${type === 'success' ? '#28a745' : 
                                 type === 'error' ? '#dc3545' : 
                                 type === 'warning' ? '#ffc107' : '#17a2b8'};
                color: white;
                padding: 15px 25px;
                border-radius: 8px;
                box-shadow: 0 5px 15px rgba(0,0,0,0.2);
                z-index: 2000;
                animation: slideIn 0.3s ease;
            `;
            
            document.body.appendChild(notification);
            
            // Hapus notifikasi setelah 3 detik
            setTimeout(() => {
                notification.style.animation = 'slideOut 0.3s ease';
                setTimeout(() => {
                    notification.remove();
                }, 300);
            }, 3000);
        }
        
        function setCurrentDate() {
            const now = new Date();
            const options = { 
                weekday: 'long', 
                year: 'numeric', 
                month: 'long', 
                day: 'numeric' 
            };
            document.getElementById('currentDate').textContent = 
                now.toLocaleDateString('id-ID', options);
        }
        
        // ==================== LOGIN & AUTH ====================
        function checkAuth() {
            const loggedInAdmin = localStorage.getItem('loggedInAdmin');
            if (loggedInAdmin) {
                currentAdmin = JSON.parse(loggedInAdmin);
                showAdminDashboard();
                return true;
            }
            return false;
        }
        
        function showAdminDashboard() {
            loginPage.style.display = 'none';
            adminDashboard.style.display = 'flex';
            
            // Update admin info
            document.getElementById('adminName').textContent = currentAdmin.name;
            document.getElementById('headerAdminName').textContent = currentAdmin.name;
            document.getElementById('adminAvatar').textContent = currentAdmin.name.charAt(0).toUpperCase();
            document.getElementById('headerAdminAvatar').textContent = currentAdmin.name.charAt(0).toUpperCase();
            
            // Set current date
            setCurrentDate();
            
            // Load initial page
            loadPage(currentPage);
        }
        
        function logout() {
            localStorage.removeItem('loggedInAdmin');
            currentAdmin = null;
            adminDashboard.style.display = 'none';
            loginPage.style.display = 'flex';
            showNotification('Berhasil logout', 'success');
        }
        
        // ==================== PAGE NAVIGATION ====================
        function loadPage(page) {
            currentPage = page;
            
            // Hide all pages
            dashboardPage.style.display = 'none';
            ordersPage.style.display = 'none';
            productsPage.style.display = 'none';
            reportsPage.style.display = 'none';
            customersPage.style.display = 'none';
            
            // Remove active class from all menu items
            document.querySelectorAll('.menu-item').forEach(item => {
                item.classList.remove('active');
            });
            
            // Show current page and set active menu
            let pageTitleText = 'Dashboard';
            
            switch(page) {
                case 'dashboard':
                    dashboardPage.style.display = 'block';
                    document.querySelector('[data-page="dashboard"]').classList.add('active');
                    pageTitleText = 'Dashboard';
                    updateDashboard();
                    break;
                    
                case 'orders':
                    ordersPage.style.display = 'block';
                    document.querySelector('[data-page="orders"]').classList.add('active');
                    pageTitleText = 'Kelola Pesanan';
                    loadOrders();
                    break;
                    
                case 'products':
                    productsPage.style.display = 'block';
                    document.querySelector('[data-page="products"]').classList.add('active');
                    pageTitleText = 'Kelola Produk';
                    loadProducts();
                    break;
                    
                case 'reports':
                    reportsPage.style.display = 'block';
                    document.querySelector('[data-page="reports"]').classList.add('active');
                    pageTitleText = 'Laporan Penjualan';
                    loadReports();
                    break;
                    
                case 'customers':
                    customersPage.style.display = 'block';
                    document.querySelector('[data-page="customers"]').classList.add('active');
                    pageTitleText = 'Data Pelanggan';
                    loadCustomers();
                    break;
            }
            
            pageTitle.textContent = pageTitleText;
            
            // Close sidebar on mobile
            if (window.innerWidth <= 992) {
                sidebar.classList.remove('active');
            }
        }
        
        // ==================== DASHBOARD FUNCTIONS ====================
        function updateDashboard() {
            // Update stats
            updateDashboardStats();
            
            // Load recent orders
            loadRecentOrders();
            
            // Update chart
            updateSalesChart();
        }
        
        function updateDashboardStats() {
            // Get today's date
            const today = new Date();
            const todayString = today.toLocaleDateString('id-ID');
            
            // Calculate stats
            const totalOrdersCount = allOrders.length;
            
            // Calculate today's revenue
            const todayRevenue = allOrders
                .filter(order => order.date === todayString)
                .reduce((sum, order) => sum + order.total, 0);
            
            // Calculate unique customers
            const uniqueCustomers = [...new Set(allOrders.map(order => order.customer.email))].length;
            
            // Get total products
            const totalProductsCount = allProducts.length;
            
            // Update DOM
            totalOrders.textContent = totalOrdersCount.toLocaleString();
            totalRevenue.textContent = formatRupiah(todayRevenue);
            totalCustomers.textContent = uniqueCustomers.toLocaleString();
            totalProducts.textContent = totalProductsCount.toLocaleString();
        }
        
        function loadRecentOrders() {
            recentOrdersTable.innerHTML = '';
            
            // Get 5 most recent orders
            const recentOrders = [...allOrders]
                .sort((a, b) => new Date(b.timestamp || 0) - new Date(a.timestamp || 0))
                .slice(0, 5);
            
            if (recentOrders.length === 0) {
                recentOrdersTable.innerHTML = `
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 40px; color: var(--gray);">
                            <i class="fas fa-box-open" style="font-size: 40px; margin-bottom: 15px; display: block;"></i>
                            <p>Belum ada pesanan</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            recentOrders.forEach(order => {
                const row = document.createElement('tr');
                
                // Calculate total items
                const totalItems = order.products.reduce((sum, product) => sum + product.quantity, 0);
                
                row.innerHTML = `
                    <td>${order.id}</td>
                    <td>${order.customer.name}</td>
                    <td>${order.date}</td>
                    <td>${formatRupiah(order.total)}</td>
                    <td><span class="status-badge ${getStatusClass(order.status)}">${getStatusText(order.status)}</span></td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn-action btn-view" onclick="viewOrder('${order.id}')" title="Lihat Detail">
                                <i class="fas fa-eye"></i>
                            </button>
                        </div>
                    </td>
                `;
                
                recentOrdersTable.appendChild(row);
            });
        }
        
        function updateSalesChart() {
            const ctx = document.getElementById('salesChart').getContext('2d');
            
            // Calculate sales for last 7 days
            const salesData = [];
            const labels = [];
            
            for (let i = 6; i >= 0; i--) {
                const date = new Date();
                date.setDate(date.getDate() - i);
                const dateString = date.toLocaleDateString('id-ID');
                
                const daySales = allOrders
                    .filter(order => order.date === dateString)
                    .reduce((sum, order) => sum + order.total, 0);
                
                salesData.push(daySales);
                labels.push(date.toLocaleDateString('id-ID', { weekday: 'short', day: 'numeric' }));
            }
            
            // Destroy existing chart if it exists
            if (salesChart) {
                salesChart.destroy();
            }
            
            // Create new chart
            salesChart = new Chart(ctx, {
                type: 'line',
                data: {
                    labels: labels,
                    datasets: [{
                        label: 'Penjualan (Rp)',
                        data: salesData,
                        backgroundColor: 'rgba(255, 107, 53, 0.1)',
                        borderColor: 'rgba(255, 107, 53, 1)',
                        borderWidth: 2,
                        tension: 0.3,
                        fill: true
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        }
                    },
                    scales: {
                        y: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    if (value >= 1000000) {
                                        return 'Rp ' + (value / 1000000).toFixed(1) + 'Jt';
                                    } else if (value >= 1000) {
                                        return 'Rp ' + (value / 1000).toFixed(0) + 'K';
                                    }
                                    return 'Rp ' + value;
                                }
                            }
                        }
                    }
                }
            });
        }
        
        // ==================== ORDERS FUNCTIONS ====================
        function loadOrders(page = 1) {
            currentOrderPage = page;
            
            // Get filter values
            const searchTerm = orderSearch.value.toLowerCase();
            const statusFilterValue = statusFilter.value;
            const dateFilterValue = dateFilter.value;
            
            // Filter orders
            let filteredOrders = allOrders;
            
            if (searchTerm) {
                filteredOrders = filteredOrders.filter(order => 
                    order.id.toLowerCase().includes(searchTerm) || 
                    order.customer.name.toLowerCase().includes(searchTerm) ||
                    order.customer.email.toLowerCase().includes(searchTerm)
                );
            }
            
            if (statusFilterValue) {
                filteredOrders = filteredOrders.filter(order => order.status === statusFilterValue);
            }
            
            if (dateFilterValue) {
                filteredOrders = filteredOrders.filter(order => {
                    const orderDate = new Date(order.date.split('/').reverse().join('-'));
                    const filterDate = new Date(dateFilterValue);
                    return orderDate.toDateString() === filterDate.toDateString();
                });
            }
            
            // Sort by date (newest first)
            filteredOrders.sort((a, b) => {
                return new Date(b.timestamp || 0) - new Date(a.timestamp || 0);
            });
            
            // Calculate pagination
            const totalOrdersCount = filteredOrders.length;
            const totalPages = Math.ceil(totalOrdersCount / ordersPerPage);
            const startIndex = (page - 1) * ordersPerPage;
            const endIndex = Math.min(startIndex + ordersPerPage, totalOrdersCount);
            const paginatedOrders = filteredOrders.slice(startIndex, endIndex);
            
            // Update table
            ordersTable.innerHTML = '';
            
            if (paginatedOrders.length === 0) {
                ordersTable.innerHTML = `
                    <tr>
                        <td colspan="7" style="text-align: center; padding: 40px; color: var(--gray);">
                            <i class="fas fa-box-open" style="font-size: 40px; margin-bottom: 15px; display: block;"></i>
                            <p>Tidak ada pesanan yang ditemukan</p>
                        </td>
                    </tr>
                `;
            } else {
                paginatedOrders.forEach(order => {
                    const row = document.createElement('tr');
                    
                    // Calculate total items
                    const totalItems = order.products.reduce((sum, product) => sum + product.quantity, 0);
                    
                    row.innerHTML = `
                        <td>${order.id}</td>
                        <td>
                            <div>${order.customer.name}</div>
                            <small style="color: var(--gray);">${order.customer.email}</small>
                        </td>
                        <td>${order.date}<br><small>${order.time}</small></td>
                        <td>${totalItems} item</td>
                        <td>${formatRupiah(order.total)}</td>
                        <td><span class="status-badge ${getStatusClass(order.status)}">${getStatusText(order.status)}</span></td>
                        <td>
                            <div class="action-buttons">
                                <button class="btn-action btn-view" onclick="viewOrder('${order.id}')" title="Lihat Detail">
                                    <i class="fas fa-eye"></i>
                                </button>
                                <button class="btn-action btn-status" onclick="changeOrderStatus('${order.id}')" title="Ubah Status">
                                    <i class="fas fa-exchange-alt"></i>
                                </button>
                            </div>
                        </td>
                    `;
                    
                    ordersTable.appendChild(row);
                });
            }
            
            // Update pagination info and buttons
            ordersPaginationInfo.textContent = `Menampilkan ${startIndex + 1}-${endIndex} dari ${totalOrdersCount} pesanan`;
            
            prevPageBtn.disabled = page <= 1;
            nextPageBtn.disabled = page >= totalPages;
        }
        
        function viewOrder(orderId) {
            const order = allOrders.find(o => o.id === orderId);
            if (!order) {
                showNotification('Pesanan tidak ditemukan', 'error');
                return;
            }
            
            // Calculate total items
            const totalItems = order.products.reduce((sum, product) => sum + product.quantity, 0);
            
            orderDetailContent.innerHTML = `
                <div class="order-details-grid">
                    <div class="detail-section">
                        <h4>Informasi Pesanan</h4>
                        <div class="detail-item">
                            <span class="detail-label">Order ID:</span>
                            <span>${order.id}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Tanggal:</span>
                            <span>${order.date} ${order.time}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Status:</span>
                            <span class="status-badge ${getStatusClass(order.status)}">${getStatusText(order.status)}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Metode Bayar:</span>
                            <span>${order.paymentMethod ? order.paymentMethod.toUpperCase() : 'QRIS'}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Catatan:</span>
                            <span>${order.notes || 'Tidak ada catatan'}</span>
                        </div>
                    </div>
                    
                    <div class="detail-section">
                        <h4>Informasi Pelanggan</h4>
                        <div class="detail-item">
                            <span class="detail-label">Nama:</span>
                            <span>${order.customer.name}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Email:</span>
                            <span>${order.customer.email}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Telepon:</span>
                            <span>${order.customer.phone}</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Alamat:</span>
                            <span>${order.customer.address}</span>
                        </div>
                    </div>
                </div>
                
                <div style="margin-top: 30px;">
                    <h4>Items Pesanan (${totalItems} item)</h4>
                    <div class="table-responsive" style="margin-top: 15px;">
                        <table class="data-table">
                            <thead>
                                <tr>
                                    <th>Produk</th>
                                    <th>Harga</th>
                                    <th>Qty</th>
                                    <th>Subtotal</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${order.products.map(product => `
                                    <tr>
                                        <td>${product.name}</td>
                                        <td>${formatRupiah(product.price)}</td>
                                        <td>${product.quantity}</td>
                                        <td>${formatRupiah(product.price * product.quantity)}</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <div style="margin-top: 30px; display: flex; justify-content: space-between; align-items: center;">
                    <div>
                        <h4>Ringkasan Pembayaran</h4>
                        <div style="background-color: #f8f9fa; padding: 15px; border-radius: 8px; width: 300px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                <span>Subtotal:</span>
                                <span>${formatRupiah(order.subtotal)}</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                <span>Pengiriman:</span>
                                <span>${formatRupiah(order.shipping)}</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                <span>Pajak (10%):</span>
                                <span>${formatRupiah(order.tax)}</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 18px; border-top: 2px solid #dee2e6; padding-top: 10px; margin-top: 10px;">
                                <span>Total:</span>
                                <span style="color: var(--primary);">${formatRupiah(order.total)}</span>
                            </div>
                        </div>
                    </div>
                    
                    <div style="display: flex; gap: 10px;">
                        <button class="btn btn-secondary" onclick="printOrderInvoice('${order.id}')">
                            <i class="fas fa-print"></i> Cetak Invoice
                        </button>
                        <button class="btn" onclick="changeOrderStatus('${order.id}')">
                            <i class="fas fa-exchange-alt"></i> Ubah Status
                        </button>
                    </div>
                </div>
            `;
            
            orderDetailModal.classList.add('active');
        }
        
        function changeOrderStatus(orderId) {
            const order = allOrders.find(o => o.id === orderId);
            if (!order) return;
            
            showConfirmModal(
                'Ubah Status Pesanan',
                `Ubah status pesanan ${orderId} dari "${getStatusText(order.status)}" menjadi:`,
                () => {
                    // Create status options
                    const statusOptions = [
                        { value: 'paid', text: 'Lunas' },
                        { value: 'processing', text: 'Diproses' },
                        { value: 'shipped', text: 'Dikirim' },
                        { value: 'delivered', text: 'Selesai' },
                        { value: 'cancelled', text: 'Dibatalkan' }
                    ];
                    
                    // Create select element
                    const select = document.createElement('select');
                    select.className = 'form-control';
                    select.style.marginTop = '10px';
                    
                    statusOptions.forEach(option => {
                        const optionEl = document.createElement('option');
                        optionEl.value = option.value;
                        optionEl.textContent = option.text;
                        optionEl.selected = order.status === option.value;
                        select.appendChild(optionEl);
                    });
                    
                    // Replace confirm modal content
                    const modalBody = document.querySelector('#confirmModal .modal-body');
                    const oldContent = modalBody.innerHTML;
                    
                    modalBody.innerHTML = `
                        <p>Ubah status pesanan ${orderId}:</p>
                        ${select.outerHTML}
                        <div style="display: flex; gap: 10px; margin-top: 20px;">
                            <button class="btn btn-secondary" id="cancelStatusChange">Batal</button>
                            <button class="btn btn-success" id="saveStatusChange">Simpan</button>
                        </div>
                    `;
                    
                    // Add event listeners
                    document.getElementById('cancelStatusChange').addEventListener('click', () => {
                        modalBody.innerHTML = oldContent;
                    });
                    
                    document.getElementById('saveStatusChange').addEventListener('click', () => {
                        const newStatus = select.value;
                        order.status = newStatus;
                        
                        // Update in localStorage
                        localStorage.setItem('customerOrders', JSON.stringify(allOrders));
                        
                        showNotification(`Status pesanan ${orderId} berhasil diubah menjadi "${getStatusText(newStatus)}"`);
                        
                        // Reload current page
                        if (currentPage === 'dashboard') {
                            updateDashboard();
                        } else if (currentPage === 'orders') {
                            loadOrders(currentOrderPage);
                        }
                        
                        confirmModal.classList.remove('active');
                    });
                },
                false // Don't show confirm button initially
            );
        }
        
        function printOrderInvoice(orderId) {
            const order = allOrders.find(o => o.id === orderId);
            if (!order) return;
            
            // Open print window
            const printWindow = window.open('', '_blank');
            
            // Create invoice HTML
            const invoiceHTML = `
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Invoice ${orderId}</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; }
                        .invoice-container { max-width: 800px; margin: 0 auto; }
                        .invoice-header { text-align: center; margin-bottom: 30px; }
                        .invoice-logo { font-size: 28px; font-weight: bold; color: #ff6b35; }
                        .invoice-table { width: 100%; border-collapse: collapse; margin: 20px 0; }
                        .invoice-table th, .invoice-table td { padding: 10px; border: 1px solid #ddd; }
                        .invoice-table th { background-color: #f5f5f5; }
                        .invoice-totals { float: right; width: 300px; }
                        @media print {
                            body { margin: 0; }
                            .no-print { display: none; }
                        }
                    </style>
                </head>
                <body>
                    <div class="invoice-container">
                        <div class="invoice-header">
                            <div class="invoice-logo">PANGS!T STORE</div>
                            <p>Jl.panongan desa panongan kec panongan kabupaten tangerang</p>
                            <p>Telepon: +62 831-9524-3139 | Email: sitirusmi54@gmail.com</p>
                        </div>
                        
                        <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin-bottom: 30px;">
                            <div>
                                <h4>Informasi Pesanan</h4>
                                <p><strong>Invoice No:</strong> ${order.id}</p>
                                <p><strong>Tanggal:</strong> ${order.date}</p>
                                <p><strong>Waktu:</strong> ${order.time}</p>
                                <p><strong>Status:</strong> ${getStatusText(order.status)}</p>
                            </div>
                            <div>
                                <h4>Informasi Pelanggan</h4>
                                <p><strong>Nama:</strong> ${order.customer.name}</p>
                                <p><strong>Telepon:</strong> ${order.customer.phone}</p>
                                <p><strong>Email:</strong> ${order.customer.email}</p>
                                <p><strong>Alamat:</strong> ${order.customer.address}</p>
                            </div>
                        </div>
                        
                        <table class="invoice-table">
                            <thead>
                                <tr>
                                    <th>Produk</th>
                                    <th>Harga</th>
                                    <th>Qty</th>
                                    <th>Subtotal</th>
                                </tr>
                            </thead>
                            <tbody>
                                ${order.products.map(product => `
                                    <tr>
                                        <td>${product.name}</td>
                                        <td>Rp ${product.price.toLocaleString()}</td>
                                        <td>${product.quantity}</td>
                                        <td>Rp ${(product.price * product.quantity).toLocaleString()}</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                        
                        <div class="invoice-totals">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                <span>Subtotal:</span>
                                <span>Rp ${order.subtotal.toLocaleString()}</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                <span>Pengiriman:</span>
                                <span>Rp ${order.shipping.toLocaleString()}</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                <span>Pajak (10%):</span>
                                <span>Rp ${order.tax.toLocaleString()}</span>
                            </div>
                            <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 20px; border-top: 2px solid #ff6b35; padding-top: 10px; margin-top: 10px;">
                                <span>TOTAL:</span>
                                <span style="color: #ff6b35;">Rp ${order.total.toLocaleString()}</span>
                            </div>
                        </div>
                        <div style="clear: both;"></div>
                        
                        <div style="margin-top: 30px; padding: 15px; background-color: #f8f9fa; border-radius: 5px;">
                            <p><strong>Metode Pembayaran:</strong> ${order.paymentMethod ? order.paymentMethod.toUpperCase() : 'QRIS'}</p>
                            <p><strong>Status Pembayaran:</strong> ${getStatusText(order.status)}</p>
                            <p><strong>Catatan:</strong> ${order.notes || 'Tidak ada catatan'}</p>
                            <p style="margin-top: 15px; font-weight: bold; color: #ff6b35;">Terima kasih telah berbelanja di PANGS!T STORE</p>
                        </div>
                    </div>
                    
                    <div class="no-print" style="text-align: center; margin-top: 30px;">
                        <button onclick="window.print()" style="padding: 10px 20px; background: #ff6b35; color: white; border: none; border-radius: 5px; cursor: pointer;">
                            Cetak Invoice
                        </button>
                        <button onclick="window.close()" style="padding: 10px 20px; background: #6c757d; color: white; border: none; border-radius: 5px; cursor: pointer; margin-left: 10px;">
                            Tutup
                        </button>
                    </div>
                </body>
                </html>
            `;
            
            printWindow.document.write(invoiceHTML);
            printWindow.document.close();
        }
        
        function exportOrders() {
            // Get filtered orders
            const searchTerm = orderSearch.value.toLowerCase();
            const statusFilterValue = statusFilter.value;
            const dateFilterValue = dateFilter.value;
            
            let filteredOrders = allOrders;
            
            if (searchTerm) {
                filteredOrders = filteredOrders.filter(order => 
                    order.id.toLowerCase().includes(searchTerm) || 
                    order.customer.name.toLowerCase().includes(searchTerm)
                );
            }
            
            if (statusFilterValue) {
                filteredOrders = filteredOrders.filter(order => order.status === statusFilterValue);
            }
            
            if (dateFilterValue) {
                filteredOrders = filteredOrders.filter(order => {
                    const orderDate = new Date(order.date.split('/').reverse().join('-'));
                    const filterDate = new Date(dateFilterValue);
                    return orderDate.toDateString() === filterDate.toDateString();
                });
            }
            
            // Create CSV content
            let csvContent = "Order ID,Pelanggan,Email,Telepon,Tanggal,Total,Status,Metode Bayar\n";
            
            filteredOrders.forEach(order => {
                const row = [
                    `"${order.id}"`,
                    `"${order.customer.name}"`,
                    `"${order.customer.email}"`,
                    `"${order.customer.phone}"`,
                    `"${order.date} ${order.time}"`,
                    `"${order.total}"`,
                    `"${getStatusText(order.status)}"`,
                    `"${order.paymentMethod || 'QRIS'}"`
                ];
                csvContent += row.join(",") + "\n";
            });
            
            // Create download link
            const blob = new Blob([csvContent], { type: 'text/csv' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `orders_${new Date().toISOString().slice(0,10)}.csv`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            window.URL.revokeObjectURL(url);
            
            showNotification('Data pesanan berhasil di-export', 'success');
        }
        
        // ==================== PRODUCTS FUNCTIONS ====================
        function loadProducts() {
            const searchTerm = productSearch.value.toLowerCase();
            
            let filteredProducts = allProducts;
            
            if (searchTerm) {
                filteredProducts = filteredProducts.filter(product => 
                    product.name.toLowerCase().includes(searchTerm) ||
                    product.description.toLowerCase().includes(searchTerm) ||
                    product.category.toLowerCase().includes(searchTerm)
                );
            }
            
            productsGridAdmin.innerHTML = '';
            
            if (filteredProducts.length === 0) {
                productsGridAdmin.innerHTML = `
                    <div style="grid-column: 1 / -1; text-align: center; padding: 40px; color: var(--gray);">
                        <i class="fas fa-dumpling" style="font-size: 60px; margin-bottom: 20px;"></i>
                        <p>Tidak ada produk yang ditemukan</p>
                        <button class="btn" id="addFirstProductBtn" style="margin-top: 15px;">
                            <i class="fas fa-plus"></i> Tambah Produk Pertama
                        </button>
                    </div>
                `;
                
                document.getElementById('addFirstProductBtn').addEventListener('click', () => {
                    openProductModal();
                });
                
                return;
            }
            
            filteredProducts.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-admin-card';
                
                productCard.innerHTML = `
                    <img src="${product.image || 'foto/default.jpg'}" alt="${product.name}" class="product-admin-img" onerror="this.src='https://via.placeholder.com/300x180?text=PANGSIT'">
                    <div class="product-admin-info">
                        <h3 class="product-admin-name">${product.name}</h3>
                        <div class="product-admin-price">${formatRupiah(product.price)}</div>
                        <div class="product-admin-category">${product.category}</div>
                        <p style="color: var(--gray); font-size: 14px; margin-bottom: 15px; height: 40px; overflow: hidden;">
                            ${product.description}
                        </p>
                        <div style="display: flex; justify-content: space-between; align-items: center;">
                            <div>
                                <span style="font-size: 12px; color: var(--gray);">Stok:</span>
                                <span style="font-weight: 600; margin-left: 5px;">${product.stock}</span>
                            </div>
                            <div class="action-buttons">
                                <button class="btn-action btn-edit" onclick="editProduct(${product.id})" title="Edit">
                                    <i class="fas fa-edit"></i>
                                </button>
                                <button class="btn-action btn-delete" onclick="deleteProduct(${product.id})" title="Hapus">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                
                productsGridAdmin.appendChild(productCard);
            });
        }
        
        function openProductModal(productId = null) {
            // Reset form
            productForm.reset();
            
            if (productId) {
                // Edit mode
                const product = allProducts.find(p => p.id === productId);
                if (!product) return;
                
                productModalTitle.textContent = 'Edit Produk';
                document.getElementById('productId').value = product.id;
                document.getElementById('productName').value = product.name;
                document.getElementById('productPrice').value = product.price;
                document.getElementById('productCategory').value = product.category;
                document.getElementById('productStock').value = product.stock || 0;
                document.getElementById('productDescription').value = product.description;
                document.getElementById('productDetails').value = product.details || '';
                document.getElementById('productImage').value = product.image || '';
            } else {
                // Add mode
                productModalTitle.textContent = 'Tambah Produk Baru';
                document.getElementById('productId').value = '';
                document.getElementById('productStock').value = 10;
            }
            
            productModal.classList.add('active');
        }
        
        function saveProduct() {
            const productId = document.getElementById('productId').value;
            const name = document.getElementById('productName').value;
            const price = parseInt(document.getElementById('productPrice').value);
            const category = document.getElementById('productCategory').value;
            const stock = parseInt(document.getElementById('productStock').value);
            const description = document.getElementById('productDescription').value;
            const details = document.getElementById('productDetails').value;
            const image = document.getElementById('productImage').value;
            
            if (!name || !price || !category || stock < 0) {
                showNotification('Harap isi semua field yang wajib diisi', 'error');
                return;
            }
            
            if (productId) {
                // Update existing product
                const index = allProducts.findIndex(p => p.id == productId);
                if (index !== -1) {
                    allProducts[index] = {
                        ...allProducts[index],
                        name,
                        price,
                        category,
                        stock,
                        description,
                        details: details || description,
                        image: image || allProducts[index].image
                    };
                }
            } else {
                // Add new product
                const newId = allProducts.length > 0 ? Math.max(...allProducts.map(p => p.id)) + 1 : 1;
                allProducts.push({
                    id: newId,
                    name,
                    price,
                    category,
                    stock,
                    description,
                    details: details || description,
                    image: image || `foto/${name.toLowerCase().replace(/\s+/g, '-')}.jpg`
                });
            }
            
            // Save to localStorage
            localStorage.setItem('adminProducts', JSON.stringify(allProducts));
            
            // Close modal and reload products
            productModal.classList.remove('active');
            loadProducts();
            
            // Update dashboard stats if on dashboard
            if (currentPage === 'dashboard') {
                updateDashboardStats();
            }
            
            showNotification(`Produk "${name}" berhasil disimpan`, 'success');
        }
        
        function editProduct(productId) {
            openProductModal(productId);
        }
        
        function deleteProduct(productId) {
            const product = allProducts.find(p => p.id === productId);
            if (!product) return;
            
            showConfirmModal(
                'Hapus Produk',
                `Apakah Anda yakin ingin menghapus produk "${product.name}"?`,
                () => {
                    // Remove product
                    allProducts = allProducts.filter(p => p.id !== productId);
                    
                    // Save to localStorage
                    localStorage.setItem('adminProducts', JSON.stringify(allProducts));
                    
                    // Reload products
                    loadProducts();
                    
                    // Update dashboard stats if on dashboard
                    if (currentPage === 'dashboard') {
                        updateDashboardStats();
                    }
                    
                    showNotification(`Produk "${product.name}" berhasil dihapus`, 'success');
                }
            );
        }
        
        // ==================== REPORTS FUNCTIONS ====================
        function loadReports() {
            // Set default date range (last 30 days)
            const today = new Date();
            const thirtyDaysAgo = new Date();
            thirtyDaysAgo.setDate(today.getDate() - 30);
            
            if (!reportDateFrom.value) {
                reportDateFrom.valueAsDate = thirtyDaysAgo;
            }
            
            if (!reportDateTo.value) {
                reportDateTo.valueAsDate = today;
            }
            
            // Filter orders by date range
            filterReport();
        }
        
        function filterReport() {
            const fromDate = new Date(reportDateFrom.value);
            const toDate = new Date(reportDateTo.value);
            
            // Reset to end of day for toDate
            toDate.setHours(23, 59, 59, 999);
            
            // Filter orders by date range
            const filteredOrders = allOrders.filter(order => {
                const orderDate = new Date(order.date.split('/').reverse().join('-'));
                return orderDate >= fromDate && orderDate <= toDate;
            });
            
            // Calculate report stats
            const totalOrdersCount = filteredOrders.length;
            const totalRevenueAmount = filteredOrders.reduce((sum, order) => sum + order.total, 0);
            const totalItemsSold = filteredOrders.reduce((sum, order) => 
                sum + order.products.reduce((itemSum, product) => itemSum + product.quantity, 0), 0);
            
            // Count unique customers in this period
            const uniqueCustomers = [...new Set(filteredOrders.map(order => order.customer.email))].length;
            
            // Update stats
            reportTotalOrders.textContent = totalOrdersCount.toLocaleString();
            reportTotalRevenue.textContent = formatRupiah(totalRevenueAmount);
            reportTotalItems.textContent = totalItemsSold.toLocaleString();
            reportTotalCustomers.textContent = uniqueCustomers.toLocaleString();
            
            // Update report table
            reportTable.innerHTML = '';
            
            if (filteredOrders.length === 0) {
                reportTable.innerHTML = `
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 40px; color: var(--gray);">
                            <i class="fas fa-chart-bar" style="font-size: 40px; margin-bottom: 15px; display: block;"></i>
                            <p>Tidak ada data penjualan dalam periode ini</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            // Sort by date (newest first)
            filteredOrders.sort((a, b) => {
                return new Date(b.timestamp || 0) - new Date(a.timestamp || 0);
            });
            
            // Display orders in table (limit to 50 for performance)
            const displayOrders = filteredOrders.slice(0, 50);
            
            displayOrders.forEach(order => {
                const row = document.createElement('tr');
                
                // Calculate total items
                const totalItems = order.products.reduce((sum, product) => sum + product.quantity, 0);
                
                row.innerHTML = `
                    <td>${order.date}<br><small>${order.time}</small></td>
                    <td>${order.id}</td>
                    <td>${order.customer.name}</td>
                    <td>${totalItems} item</td>
                    <td>${formatRupiah(order.total)}</td>
                    <td><span class="status-badge ${getStatusClass(order.status)}">${getStatusText(order.status)}</span></td>
                `;
                
                reportTable.appendChild(row);
            });
            
            // Show message if there are more orders
            if (filteredOrders.length > 50) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td colspan="6" style="text-align: center; color: var(--gray); font-style: italic; padding: 15px;">
                        Dan ${filteredOrders.length - 50} pesanan lainnya...
                    </td>
                `;
                reportTable.appendChild(row);
            }
        }
        
        function exportReport() {
            const fromDate = new Date(reportDateFrom.value);
            const toDate = new Date(reportDateTo.value);
            
            // Reset to end of day for toDate
            toDate.setHours(23, 59, 59, 999);
            
            // Filter orders by date range
            const filteredOrders = allOrders.filter(order => {
                const orderDate = new Date(order.date.split('/').reverse().join('-'));
                return orderDate >= fromDate && orderDate <= toDate;
            });
            
            // Sort by date
            filteredOrders.sort((a, b) => {
                return new Date(a.timestamp || 0) - new Date(b.timestamp || 0);
            });
            
            // Create CSV content
            let csvContent = "Tanggal,Order ID,Pelanggan,Email,Items,Total,Status,Metode Bayar\n";
            
            filteredOrders.forEach(order => {
                const totalItems = order.products.reduce((sum, product) => sum + product.quantity, 0);
                
                const row = [
                    `"${order.date} ${order.time}"`,
                    `"${order.id}"`,
                    `"${order.customer.name}"`,
                    `"${order.customer.email}"`,
                    `"${totalItems}"`,
                    `"${order.total}"`,
                    `"${getStatusText(order.status)}"`,
                    `"${order.paymentMethod || 'QRIS'}"`
                ];
                csvContent += row.join(",") + "\n";
            });
            
            // Create download link
            const blob = new Blob([csvContent], { type: 'text/csv' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `laporan_penjualan_${reportDateFrom.value}_to_${reportDateTo.value}.csv`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            window.URL.revokeObjectURL(url);
            
            showNotification('Laporan penjualan berhasil di-export', 'success');
        }
        
        // ==================== CUSTOMERS FUNCTIONS ====================
        function loadCustomers() {
            const searchTerm = customerSearch.value.toLowerCase();
            
            // Extract unique customers from orders
            const customersMap = new Map();
            
            allOrders.forEach(order => {
                const email = order.customer.email;
                if (!customersMap.has(email)) {
                    customersMap.set(email, {
                        name: order.customer.name,
                        email: order.customer.email,
                        phone: order.customer.phone,
                        totalOrders: 0,
                        totalSpent: 0,
                        lastOrder: null
                    });
                }
                
                const customer = customersMap.get(email);
                customer.totalOrders += 1;
                customer.totalSpent += order.total;
                
                // Update last order date
                const orderDate = new Date(order.timestamp || order.date.split('/').reverse().join('-'));
                if (!customer.lastOrder || orderDate > customer.lastOrder) {
                    customer.lastOrder = orderDate;
                }
            });
            
            // Convert to array and filter
            let customers = Array.from(customersMap.values());
            
            if (searchTerm) {
                customers = customers.filter(customer => 
                    customer.name.toLowerCase().includes(searchTerm) ||
                    customer.email.toLowerCase().includes(searchTerm)
                );
            }
            
            // Sort by total spent (highest first)
            customers.sort((a, b) => b.totalSpent - a.totalSpent);
            
            // Update table
            customersTable.innerHTML = '';
            
            if (customers.length === 0) {
                customersTable.innerHTML = `
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 40px; color: var(--gray);">
                            <i class="fas fa-users" style="font-size: 40px; margin-bottom: 15px; display: block;"></i>
                            <p>Tidak ada data pelanggan</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            customers.forEach(customer => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>${customer.name}</td>
                    <td>${customer.email}</td>
                    <td>${customer.phone}</td>
                    <td>${customer.totalOrders}</td>
                    <td>${formatRupiah(customer.totalSpent)}</td>
                    <td>${customer.lastOrder ? customer.lastOrder.toLocaleDateString('id-ID') : '-'}</td>
                `;
                
                customersTable.appendChild(row);
            });
        }
        
        // ==================== MODAL FUNCTIONS ====================
        function showConfirmModal(title, message, confirmCallback, showConfirmButton = true) {
            confirmModalTitle.textContent = title;
            confirmModalMessage.textContent = message;
            
            confirmModal.classList.add('active');
            
            // Set up confirm button
            const confirmAction = () => {
                confirmModal.classList.remove('active');
                if (confirmCallback) confirmCallback();
            };
            
            confirmActionBtn.onclick = confirmAction;
            
            // Show or hide confirm button
            confirmActionBtn.style.display = showConfirmButton ? 'block' : 'none';
        }
        
        // ==================== EVENT LISTENERS ====================
        document.addEventListener('DOMContentLoaded', () => {
            // Check if user is already logged in
            if (!checkAuth()) {
                loginPage.style.display = 'flex';
                adminDashboard.style.display = 'none';
            }
            
            // Login form
            loginForm.addEventListener('submit', (e) => {
                e.preventDefault();
                
                const username = document.getElementById('adminUsername').value;
                const password = document.getElementById('adminPassword').value;
                
                if (username === adminData.username && password === adminData.password) {
                    currentAdmin = {
                        username: username,
                        name: adminData.name
                    };
                    
                    localStorage.setItem('loggedInAdmin', JSON.stringify(currentAdmin));
                    showAdminDashboard();
                    showNotification('Login berhasil!', 'success');
                } else {
                    showNotification('Username atau password salah!', 'error');
                }
            });
            
            // Logout button
            logoutBtn.addEventListener('click', logout);
            
            // Menu toggle for mobile
            menuToggle.addEventListener('click', () => {
                sidebar.classList.toggle('active');
            });
            
            // Sidebar menu items
            document.querySelectorAll('.menu-item').forEach(item => {
                item.addEventListener('click', (e) => {
                    e.preventDefault();
                    const page = item.getAttribute('data-page');
                    loadPage(page);
                });
            });
            
            // Order Detail Modal
            closeOrderModal.addEventListener('click', () => {
                orderDetailModal.classList.remove('active');
            });
            
            orderDetailModal.addEventListener('click', (e) => {
                if (e.target === orderDetailModal) {
                    orderDetailModal.classList.remove('active');
                }
            });
            
            // Product Modal
            closeProductModal.addEventListener('click', () => {
                productModal.classList.remove('active');
            });
            
            cancelProductBtn.addEventListener('click', () => {
                productModal.classList.remove('active');
            });
            
            productModal.addEventListener('click', (e) => {
                if (e.target === productModal) {
                    productModal.classList.remove('active');
                }
            });
            
            productForm.addEventListener('submit', (e) => {
                e.preventDefault();
                saveProduct();
            });
            
            // Confirm Modal
            closeConfirmModal.addEventListener('click', () => {
                confirmModal.classList.remove('active');
            });
            
            cancelConfirmBtn.addEventListener('click', () => {
                confirmModal.classList.remove('active');
            });
            
            confirmModal.addEventListener('click', (e) => {
                if (e.target === confirmModal) {
                    confirmModal.classList.remove('active');
                }
            });
            
            // Orders page events
            orderSearch.addEventListener('input', () => {
                loadOrders(1);
            });
            
            statusFilter.addEventListener('change', () => {
                loadOrders(1);
            });
            
            dateFilter.addEventListener('change', () => {
                loadOrders(1);
            });
            
            exportOrdersBtn.addEventListener('click', exportOrders);
            
            prevPageBtn.addEventListener('click', () => {
                if (currentOrderPage > 1) {
                    loadOrders(currentOrderPage - 1);
                }
            });
            
            nextPageBtn.addEventListener('click', () => {
                loadOrders(currentOrderPage + 1);
            });
            
            // Products page events
            addProductBtn.addEventListener('click', () => {
                openProductModal();
            });
            
            productSearch.addEventListener('input', loadProducts);
            
            // Reports page events
            filterReportBtn.addEventListener('click', filterReport);
            
            resetReportBtn.addEventListener('click', () => {
                // Reset to last 30 days
                const today = new Date();
                const thirtyDaysAgo = new Date();
                thirtyDaysAgo.setDate(today.getDate() - 30);
                
                reportDateFrom.valueAsDate = thirtyDaysAgo;
                reportDateTo.valueAsDate = today;
                
                filterReport();
            });
            
            exportReportBtn.addEventListener('click', exportReport);
            
            // Customers page events
            customerSearch.addEventListener('input', loadCustomers);
            
            // Add animation CSS for notifications
            const style = document.createElement('style');
            style.textContent = `
                @keyframes slideIn {
                    from {
                        transform: translateX(100%);
                        opacity: 0;
                    }
                    to {
                        transform: translateX(0);
                        opacity: 1;
                    }
                }
                
                @keyframes slideOut {
                    from {
                        transform: translateX(0);
                        opacity: 1;
                    }
                    to {
                        transform: translateX(100%);
                        opacity: 0;
                    }
                }
            `;
            document.head.appendChild(style);
            
            console.log('✅ Admin Panel PANGS!T siap digunakan');
        });
    </script>
</body>
</html>
