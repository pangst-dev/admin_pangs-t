<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin PANGS!T - Dashboard</title>
    
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
        
        .container {
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
            transition: var(--transition);
            z-index: 100;
            overflow-y: auto;
        }
        
        .sidebar-header {
            padding: 25px 20px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            text-align: center;
        }
        
        .admin-logo {
            font-size: 24px;
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            color: white;
        }
        
        .admin-logo span {
            color: var(--primary);
        }
        
        .sidebar-menu {
            padding: 20px 0;
        }
        
        .menu-item {
            display: block;
            padding: 15px 20px;
            color: rgba(255, 255, 255, 0.8);
            text-decoration: none;
            transition: var(--transition);
            border-left: 3px solid transparent;
            display: flex;
            align-items: center;
            gap: 12px;
        }
        
        .menu-item:hover {
            background-color: rgba(255, 255, 255, 0.05);
            color: white;
        }
        
        .menu-item.active {
            background-color: rgba(255, 107, 53, 0.1);
            color: white;
            border-left: 3px solid var(--primary);
        }
        
        .menu-item i {
            width: 20px;
            text-align: center;
        }
        
        /* Main Content */
        .main-content {
            flex: 1;
            margin-left: var(--sidebar-width);
            transition: var(--transition);
        }
        
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
            z-index: 90;
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
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
        }
        
        .logout-btn {
            background-color: var(--danger);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
        }
        
        .logout-btn:hover {
            background-color: #c82333;
        }
        
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 24px;
            color: var(--secondary);
            cursor: pointer;
        }
        
        /* Content Area */
        .content {
            padding: 30px;
        }
        
        .content-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }
        
        .content-title {
            font-size: 28px;
            color: var(--secondary);
        }
        
        /* Dashboard Stats */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
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
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }
        
        .stat-icon {
            width: 60px;
            height: 60px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: white;
        }
        
        .stat-info h3 {
            font-size: 14px;
            color: var(--gray);
            margin-bottom: 5px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .stat-number {
            font-size: 32px;
            font-weight: 700;
            color: var(--secondary);
        }
        
        .stat-change {
            font-size: 12px;
            margin-top: 5px;
        }
        
        .change-up {
            color: var(--success);
        }
        
        .change-down {
            color: var(--danger);
        }
        
        /* Table Styles */
        .table-container {
            background-color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            overflow: hidden;
            margin-bottom: 30px;
        }
        
        .table-header {
            padding: 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .table-title {
            font-size: 20px;
            color: var(--secondary);
        }
        
        .table-actions {
            display: flex;
            gap: 10px;
        }
        
        .btn {
            padding: 10px 20px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-primary {
            background-color: var(--primary);
            color: white;
        }
        
        .btn-primary:hover {
            background-color: var(--primary-dark);
        }
        
        .btn-secondary {
            background-color: var(--secondary);
            color: white;
        }
        
        .btn-secondary:hover {
            background-color: #1f2135;
        }
        
        .btn-outline {
            background-color: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }
        
        .btn-outline:hover {
            background-color: var(--primary);
            color: white;
        }
        
        .btn-success {
            background-color: var(--success);
            color: white;
        }
        
        .btn-warning {
            background-color: var(--warning);
            color: var(--dark);
        }
        
        .btn-danger {
            background-color: var(--danger);
            color: white;
        }
        
        .btn-sm {
            padding: 6px 12px;
            font-size: 14px;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        thead {
            background-color: var(--light-gray);
        }
        
        th {
            padding: 15px;
            text-align: left;
            font-weight: 600;
            color: var(--secondary);
            border-bottom: 1px solid var(--light-gray);
        }
        
        td {
            padding: 15px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        tbody tr:hover {
            background-color: rgba(0, 0, 0, 0.02);
        }
        
        .status-badge {
            display: inline-block;
            padding: 5px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .status-lunas {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status-pending {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .status-processing {
            background-color: #d1ecf1;
            color: #0c5460;
        }
        
        .status-shipped {
            background-color: #cce5ff;
            color: #004085;
        }
        
        .status-delivered {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status-cancelled {
            background-color: #f8d7da;
            color: #721c24;
        }
        
        /* Filter Section */
        .filter-container {
            background-color: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }
        
        .filter-title {
            font-size: 18px;
            color: var(--secondary);
            margin-bottom: 15px;
        }
        
        .filter-form {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
        }
        
        .form-group {
            margin-bottom: 0;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary);
            font-size: 14px;
        }
        
        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid var(--light-gray);
            border-radius: 5px;
            font-size: 14px;
            transition: var(--transition);
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            z-index: 2000;
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
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        }
        
        .close-modal {
            position: absolute;
            top: 20px;
            right: 20px;
            background: none;
            border: none;
            font-size: 28px;
            color: var(--gray);
            cursor: pointer;
            z-index: 10;
        }
        
        .modal-header {
            padding: 25px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .modal-title {
            font-size: 24px;
            color: var(--secondary);
        }
        
        .modal-body {
            padding: 25px;
        }
        
        .order-detail-section {
            margin-bottom: 25px;
        }
        
        .order-detail-title {
            font-size: 18px;
            color: var(--secondary);
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .order-info-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .info-item {
            margin-bottom: 10px;
        }
        
        .info-label {
            font-weight: 600;
            color: var(--secondary);
            margin-bottom: 5px;
        }
        
        .info-value {
            color: var(--dark);
        }
        
        .products-table {
            margin-top: 20px;
        }
        
        .products-table th, .products-table td {
            padding: 12px;
        }
        
        .order-total {
            text-align: right;
            margin-top: 20px;
            padding-top: 20px;
            border-top: 2px solid var(--light-gray);
        }
        
        .total-amount {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .status-update-form {
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid var(--light-gray);
        }
        
        .status-update-form h4 {
            margin-bottom: 15px;
            color: var(--secondary);
        }
        
        .status-options {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }
        
        .status-option {
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .status-option input {
            margin: 0;
        }
        
        .modal-footer {
            padding: 20px 25px;
            border-top: 1px solid var(--light-gray);
            display: flex;
            justify-content: flex-end;
            gap: 15px;
        }
        
        /* Login Page */
        .login-container {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(135deg, var(--primary) 0%, var(--secondary) 100%);
            padding: 20px;
        }
        
        .login-box {
            background-color: white;
            border-radius: 15px;
            padding: 40px;
            box-shadow: var(--shadow);
            width: 100%;
            max-width: 400px;
            text-align: center;
        }
        
        .login-logo {
            font-size: 32px;
            font-weight: 700;
            color: var(--secondary);
            margin-bottom: 10px;
        }
        
        .login-logo span {
            color: var(--primary);
        }
        
        .login-subtitle {
            color: var(--gray);
            margin-bottom: 30px;
        }
        
        .login-form .form-group {
            margin-bottom: 20px;
            text-align: left;
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
            
            .mobile-menu-btn {
                display: block;
            }
        }
        
        @media (max-width: 768px) {
            .header {
                padding: 0 15px;
            }
            
            .content {
                padding: 15px;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            table {
                display: block;
                overflow-x: auto;
            }
            
            .filter-form {
                grid-template-columns: 1fr;
            }
            
            .order-info-grid {
                grid-template-columns: 1fr;
            }
            
            .modal-content {
                max-height: 95vh;
            }
        }
        
        /* Alert */
        .alert {
            padding: 15px;
            border-radius: 5px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }
        
        .alert-success {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .alert-error {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
        
        .close-alert {
            background: none;
            border: none;
            font-size: 20px;
            cursor: pointer;
            color: inherit;
        }
        
        /* Search Bar */
        .search-bar {
            position: relative;
            width: 300px;
        }
        
        .search-bar input {
            width: 100%;
            padding: 10px 15px 10px 40px;
            border: 1px solid var(--light-gray);
            border-radius: 5px;
            font-size: 14px;
        }
        
        .search-bar i {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
        }
        
        /* Pagination */
        .pagination {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 10px;
            margin-top: 20px;
        }
        
        .page-link {
            padding: 8px 12px;
            border: 1px solid var(--light-gray);
            border-radius: 5px;
            background-color: white;
            color: var(--secondary);
            cursor: pointer;
            transition: var(--transition);
        }
        
        .page-link:hover {
            background-color: var(--light-gray);
        }
        
        .page-link.active {
            background-color: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        .page-link.disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div id="loginPage" class="login-container">
        <div class="login-box">
            <div class="login-logo">PANGS!T <span>Admin</span></div>
            <p class="login-subtitle">Dashboard Admin Toko Online</p>
            
            <form id="loginForm" class="login-form">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" class="form-control" required>
                </div>
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" class="form-control" required>
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%; padding: 12px;">Login</button>
            </form>
            
            <div style="margin-top: 20px; font-size: 14px; color: var(--gray);">
                <p>Default login:</p>
                <p>Username: <strong>admin</strong></p>
                <p>Password: <strong>admin123</strong></p>
            </div>
        </div>
    </div>
    
    <!-- Admin Dashboard -->
    <div id="adminDashboard" class="container" style="display: none;">
        <!-- Sidebar -->
        <div class="sidebar" id="sidebar">
            <div class="sidebar-header">
                <div class="admin-logo">
                    <i class="fas fa-dumpling"></i>
                    <span>PANGS!T</span> Admin
                </div>
            </div>
            
            <div class="sidebar-menu">
                <a href="#" class="menu-item active" data-page="dashboard">
                    <i class="fas fa-tachometer-alt"></i>
                    <span>Dashboard</span>
                </a>
                <a href="#" class="menu-item" data-page="orders">
                    <i class="fas fa-shopping-cart"></i>
                    <span>Pesanan</span>
                    <span class="badge" id="pendingCount" style="margin-left: auto; background: var(--warning); color: var(--dark); padding: 2px 8px; border-radius: 10px; font-size: 12px;">0</span>
                </a>
                <a href="#" class="menu-item" data-page="products">
                    <i class="fas fa-box"></i>
                    <span>Produk</span>
                </a>
                <a href="#" class="menu-item" data-page="customers">
                    <i class="fas fa-users"></i>
                    <span>Pelanggan</span>
                </a>
                <a href="#" class="menu-item" data-page="reports">
                    <i class="fas fa-chart-bar"></i>
                    <span>Laporan</span>
                </a>
                <a href="#" class="menu-item" data-page="settings">
                    <i class="fas fa-cog"></i>
                    <span>Pengaturan</span>
                </a>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content" id="mainContent">
            <!-- Header -->
            <div class="header">
                <div class="header-left">
                    <button class="mobile-menu-btn" id="mobileMenuBtn">
                        <i class="fas fa-bars"></i>
                    </button>
                    <h1 id="pageTitle">Dashboard</h1>
                </div>
                
                <div class="header-right">
                    <div class="search-bar">
                        <i class="fas fa-search"></i>
                        <input type="text" id="searchInput" placeholder="Cari pesanan...">
                    </div>
                    <div class="admin-info">
                        <div class="admin-avatar">
                            <span id="adminInitial">A</span>
                        </div>
                        <div>
                            <div style="font-weight: 600;">Administrator</div>
                            <div style="font-size: 12px; color: var(--gray);">Admin Panel</div>
                        </div>
                    </div>
                    <button class="logout-btn" id="logoutBtn">
                        <i class="fas fa-sign-out-alt"></i> Logout
                    </button>
                </div>
            </div>
            
            <!-- Content Area -->
            <div class="content">
                <!-- Dashboard Page -->
                <div id="dashboardPage" class="page-content">
                    <div class="content-header">
                        <div>
                            <h2 class="content-title">Dashboard Admin</h2>
                            <p style="color: var(--gray);">Ringkasan statistik toko PANGS!T</p>
                        </div>
                        <div class="table-actions">
                            <button class="btn btn-primary" id="refreshData">
                                <i class="fas fa-sync-alt"></i> Refresh Data
                            </button>
                        </div>
                    </div>
                    
                    <!-- Stats Cards -->
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--primary);">
                                <i class="fas fa-shopping-cart"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Total Pesanan</h3>
                                <div class="stat-number" id="totalOrders">0</div>
                                <div class="stat-change change-up">
                                    <i class="fas fa-arrow-up"></i> 12% dari bulan lalu
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--success);">
                                <i class="fas fa-money-bill-wave"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Pendapatan</h3>
                                <div class="stat-number" id="totalRevenue">Rp 0</div>
                                <div class="stat-change change-up">
                                    <i class="fas fa-arrow-up"></i> 8% dari bulan lalu
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--info);">
                                <i class="fas fa-users"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Pelanggan</h3>
                                <div class="stat-number" id="totalCustomers">0</div>
                                <div class="stat-change change-up">
                                    <i class="fas fa-arrow-up"></i> 5% dari bulan lalu
                                </div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--warning);">
                                <i class="fas fa-clock"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Menunggu Diproses</h3>
                                <div class="stat-number" id="pendingOrders">0</div>
                                <div class="stat-change change-down">
                                    <i class="fas fa-arrow-down"></i> 3% dari kemarin
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Recent Orders -->
                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">Pesanan Terbaru</h3>
                            <div class="table-actions">
                                <button class="btn btn-outline btn-sm" id="viewAllOrders">
                                    <i class="fas fa-list"></i> Lihat Semua
                                </button>
                            </div>
                        </div>
                        
                        <table>
                            <thead>
                                <tr>
                                    <th>ID Pesanan</th>
                                    <th>Tanggal</th>
                                    <th>Pelanggan</th>
                                    <th>Total</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="recentOrdersTable">
                                <!-- Data pesanan terbaru akan ditampilkan di sini -->
                                <tr>
                                    <td colspan="6" style="text-align: center; padding: 40px;">
                                        <i class="fas fa-box-open" style="font-size: 48px; color: var(--light-gray); margin-bottom: 15px; display: block;"></i>
                                        <p style="color: var(--gray);">Belum ada pesanan</p>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Orders Page -->
                <div id="ordersPage" class="page-content" style="display: none;">
                    <div class="content-header">
                        <div>
                            <h2 class="content-title">Kelola Pesanan</h2>
                            <p style="color: var(--gray);">Kelola dan update status pesanan pelanggan</p>
                        </div>
                        <div class="table-actions">
                            <button class="btn btn-primary" id="exportOrders">
                                <i class="fas fa-file-export"></i> Export Data
                            </button>
                        </div>
                    </div>
                    
                    <!-- Filter Section -->
                    <div class="filter-container">
                        <h4 class="filter-title">Filter Pesanan</h4>
                        <div class="filter-form">
                            <div class="form-group">
                                <label>Status Pesanan</label>
                                <select id="filterStatus" class="form-control">
                                    <option value="all">Semua Status</option>
                                    <option value="lunas">LUNAS</option>
                                    <option value="processing">Sedang Diproses</option>
                                    <option value="shipped">Dalam Pengiriman</option>
                                    <option value="delivered">Telah Dikirim</option>
                                    <option value="cancelled">Dibatalkan</option>
                                </select>
                            </div>
                            <div class="form-group">
                                <label>Tanggal Mulai</label>
                                <input type="date" id="filterStartDate" class="form-control">
                            </div>
                            <div class="form-group">
                                <label>Tanggal Akhir</label>
                                <input type="date" id="filterEndDate" class="form-control">
                            </div>
                            <div class="form-group">
                                <label>&nbsp;</label>
                                <button class="btn btn-secondary" id="applyFilter">
                                    <i class="fas fa-filter"></i> Terapkan Filter
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Orders Table -->
                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">Daftar Pesanan</h3>
                            <div class="table-actions">
                                <div style="display: flex; align-items: center; gap: 10px;">
                                    <span style="font-size: 14px; color: var(--gray);">Total: <strong id="ordersCount">0</strong> pesanan</span>
                                </div>
                            </div>
                        </div>
                        
                        <table>
                            <thead>
                                <tr>
                                    <th>ID Pesanan</th>
                                    <th>Tanggal</th>
                                    <th>Pelanggan</th>
                                    <th>Metode Bayar</th>
                                    <th>Total</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="ordersTable">
                                <!-- Data pesanan akan ditampilkan di sini -->
                            </tbody>
                        </table>
                        
                        <!-- Pagination -->
                        <div class="pagination" id="ordersPagination">
                            <!-- Pagination akan di-generate oleh JavaScript -->
                        </div>
                    </div>
                </div>
                
                <!-- Products Page -->
                <div id="productsPage" class="page-content" style="display: none;">
                    <div class="content-header">
                        <div>
                            <h2 class="content-title">Kelola Produk</h2>
                            <p style="color: var(--gray);">Kelola produk yang dijual di toko</p>
                        </div>
                        <div class="table-actions">
                            <button class="btn btn-primary" id="addProductBtn">
                                <i class="fas fa-plus"></i> Tambah Produk
                            </button>
                        </div>
                    </div>
                    
                    <!-- Products Table -->
                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">Daftar Produk</h3>
                            <div class="table-actions">
                                <div style="display: flex; align-items: center; gap: 10px;">
                                    <span style="font-size: 14px; color: var(--gray);">Total: <strong id="productsCount">0</strong> produk</span>
                                </div>
                            </div>
                        </div>
                        
                        <table>
                            <thead>
                                <tr>
                                    <th>ID</th>
                                    <th>Gambar</th>
                                    <th>Nama Produk</th>
                                    <th>Harga</th>
                                    <th>Kategori</th>
                                    <th>Status</th>
                                    <th>Aksi</th>
                                </tr>
                            </thead>
                            <tbody id="productsTable">
                                <!-- Data produk akan ditampilkan di sini -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Customers Page -->
                <div id="customersPage" class="page-content" style="display: none;">
                    <div class="content-header">
                        <div>
                            <h2 class="content-title">Data Pelanggan</h2>
                            <p style="color: var(--gray);">Data pelanggan yang pernah berbelanja</p>
                        </div>
                    </div>
                    
                    <!-- Customers Table -->
                    <div class="table-container">
                        <div class="table-header">
                            <h3 class="table-title">Daftar Pelanggan</h3>
                            <div class="table-actions">
                                <div style="display: flex; align-items: center; gap: 10px;">
                                    <span style="font-size: 14px; color: var(--gray);">Total: <strong id="customersCount">0</strong> pelanggan</span>
                                </div>
                            </div>
                        </div>
                        
                        <table>
                            <thead>
                                <tr>
                                    <th>Nama</th>
                                    <th>Email</th>
                                    <th>Telepon</th>
                                    <th>Total Pesanan</th>
                                    <th>Total Belanja</th>
                                    <th>Terakhir Pesan</th>
                                </tr>
                            </thead>
                            <tbody id="customersTable">
                                <!-- Data pelanggan akan ditampilkan di sini -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Reports Page -->
                <div id="reportsPage" class="page-content" style="display: none;">
                    <div class="content-header">
                        <div>
                            <h2 class="content-title">Laporan Penjualan</h2>
                            <p style="color: var(--gray);">Analisis dan laporan penjualan toko</p>
                        </div>
                        <div class="table-actions">
                            <button class="btn btn-primary" id="generateReport">
                                <i class="fas fa-download"></i> Unduh Laporan
                            </button>
                        </div>
                    </div>
                    
                    <!-- Report Filters -->
                    <div class="filter-container">
                        <h4 class="filter-title">Filter Laporan</h4>
                        <div class="filter-form">
                            <div class="form-group">
                                <label>Periode Laporan</label>
                                <select id="reportPeriod" class="form-control">
                                    <option value="today">Hari Ini</option>
                                    <option value="yesterday">Kemarin</option>
                                    <option value="week">Minggu Ini</option>
                                    <option value="month" selected>Bulan Ini</option>
                                    <option value="last_month">Bulan Lalu</option>
                                    <option value="year">Tahun Ini</option>
                                    <option value="custom">Kustom</option>
                                </select>
                            </div>
                            <div class="form-group" id="customDateRange" style="display: none;">
                                <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 10px;">
                                    <div>
                                        <label>Tanggal Mulai</label>
                                        <input type="date" id="reportStartDate" class="form-control">
                                    </div>
                                    <div>
                                        <label>Tanggal Akhir</label>
                                        <input type="date" id="reportEndDate" class="form-control">
                                    </div>
                                </div>
                            </div>
                            <div class="form-group">
                                <label>&nbsp;</label>
                                <button class="btn btn-secondary" id="applyReportFilter">
                                    <i class="fas fa-chart-bar"></i> Tampilkan Laporan
                                </button>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Report Stats -->
                    <div class="stats-grid">
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--primary);">
                                <i class="fas fa-shopping-cart"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Total Transaksi</h3>
                                <div class="stat-number" id="reportTransactions">0</div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--success);">
                                <i class="fas fa-money-bill-wave"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Total Pendapatan</h3>
                                <div class="stat-number" id="reportRevenue">Rp 0</div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--info);">
                                <i class="fas fa-box"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Produk Terjual</h3>
                                <div class="stat-number" id="reportProductsSold">0</div>
                            </div>
                        </div>
                        
                        <div class="stat-card">
                            <div class="stat-icon" style="background-color: var(--warning);">
                                <i class="fas fa-percentage"></i>
                            </div>
                            <div class="stat-info">
                                <h3>Rata-rata Pesanan</h3>
                                <div class="stat-number" id="reportAvgOrder">Rp 0</div>
                            </div>
                        </div>
                    </div>
                    
                    <!-- Top Products -->
                    <div class="table-container" style="margin-top: 30px;">
                        <div class="table-header">
                            <h3 class="table-title">Produk Terlaris</h3>
                        </div>
                        
                        <table>
                            <thead>
                                <tr>
                                    <th>Produk</th>
                                    <th>Terjual</th>
                                    <th>Pendapatan</th>
                                    <th>Persentase</th>
                                </tr>
                            </thead>
                            <tbody id="topProductsTable">
                                <!-- Data produk terlaris akan ditampilkan di sini -->
                            </tbody>
                        </table>
                    </div>
                </div>
                
                <!-- Settings Page -->
                <div id="settingsPage" class="page-content" style="display: none;">
                    <div class="content-header">
                        <div>
                            <h2 class="content-title">Pengaturan Sistem</h2>
                            <p style="color: var(--gray);">Konfigurasi sistem admin toko online</p>
                        </div>
                    </div>
                    
                    <!-- Settings Form -->
                    <div class="filter-container">
                        <h4 class="filter-title">Informasi Toko</h4>
                        <form id="storeSettingsForm">
                            <div class="form-group">
                                <label>Nama Toko</label>
                                <input type="text" id="storeName" class="form-control" value="PANGS!T Store" required>
                            </div>
                            <div class="form-group">
                                <label>Email Toko</label>
                                <input type="email" id="storeEmail" class="form-control" value="sitirusmi54@gmail.com" required>
                            </div>
                            <div class="form-group">
                                <label>Telepon Toko</label>
                                <input type="tel" id="storePhone" class="form-control" value="+62 831-9524-3139" required>
                            </div>
                            <div class="form-group">
                                <label>Alamat Toko</label>
                                <textarea id="storeAddress" class="form-control" rows="3" required>Jl.panongan desa panongan kec panongan kabupaten tangerang</textarea>
                            </div>
                            <div class="form-group">
                                <label>Biaya Pengiriman (Rp)</label>
                                <input type="number" id="shippingFee" class="form-control" value="15000" required>
                            </div>
                            <button type="submit" class="btn btn-primary">
                                <i class="fas fa-save"></i> Simpan Pengaturan
                            </button>
                        </form>
                    </div>
                    
                    <!-- Admin Account -->
                    <div class="filter-container" style="margin-top: 30px;">
                        <h4 class="filter-title">Akun Admin</h4>
                        <form id="adminAccountForm">
                            <div class="form-group">
                                <label>Username</label>
                                <input type="text" id="adminUsername" class="form-control" value="admin" readonly>
                            </div>
                            <div class="form-group">
                                <label>Password Baru</label>
                                <input type="password" id="adminPassword" class="form-control" placeholder="Kosongkan jika tidak ingin mengubah">
                            </div>
                            <div class="form-group">
                                <label>Konfirmasi Password</label>
                                <input type="password" id="adminConfirmPassword" class="form-control">
                            </div>
                            <button type="submit" class="btn btn-primary">
                                <i class="fas fa-key"></i> Update Password
                            </button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modal Detail Pesanan -->
    <div class="modal" id="orderDetailModal">
        <div class="modal-content">
            <button class="close-modal" id="closeOrderModal">&times;</button>
            <div class="modal-header">
                <h3 class="modal-title">Detail Pesanan</h3>
            </div>
            <div class="modal-body">
                <div id="orderDetailContent">
                    <!-- Konten detail pesanan akan diisi di sini -->
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modal Tambah/Edit Produk -->
    <div class="modal" id="productModal">
        <div class="modal-content">
            <button class="close-modal" id="closeProductModal">&times;</button>
            <div class="modal-header">
                <h3 class="modal-title" id="productModalTitle">Tambah Produk Baru</h3>
            </div>
            <div class="modal-body">
                <form id="productForm">
                    <input type="hidden" id="productId">
                    <div class="form-group">
                        <label>Nama Produk</label>
                        <input type="text" id="productName" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label>Harga (Rp)</label>
                        <input type="number" id="productPrice" class="form-control" required>
                    </div>
                    <div class="form-group">
                        <label>Kategori</label>
                        <select id="productCategory" class="form-control" required>
                            <option value="pedas">Pedas</option>
                            <option value="original">Original</option>
                            <option value="ayam isi 4">Ayam Isi 4</option>
                            <option value="udang">Udang</option>
                            <option value="spesial">Spesial</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Deskripsi</label>
                        <textarea id="productDescription" class="form-control" rows="3" required></textarea>
                    </div>
                    <div class="form-group">
                        <label>URL Gambar</label>
                        <input type="text" id="productImage" class="form-control" placeholder="contoh: foto/nama-produk.jpg" required>
                    </div>
                    <div class="form-group">
                        <label>Detail Produk</label>
                        <textarea id="productDetails" class="form-control" rows="3" required></textarea>
                    </div>
                    <div class="form-group">
                        <label>Status</label>
                        <select id="productStatus" class="form-control" required>
                            <option value="active">Aktif</option>
                            <option value="inactive">Tidak Aktif</option>
                        </select>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-outline" id="cancelProduct">Batal</button>
                        <button type="submit" class="btn btn-primary" id="saveProduct">Simpan Produk</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
    
    <script>
        // ==================== KONFIGURASI ADMIN ====================
        
        // Data Admin (untuk demo)
        const adminCredentials = {
            username: "admin",
            password: "admin123"
        };
        
        // Data produk dari toko utama
        let products = JSON.parse(localStorage.getItem('products')) || [
            {
                id: 1,
                name: "fire silk wonton",
                price: 20000,
                image: "foto/fire silk wonton.jpg",
                description: "Kesan: lembut, pedas aromatik, classy dengan minyak cabai khas Asia.",
                details: "Kesan: lembut, pedas aromatik, classy dengan minyak cabai khas Asia.",
                category: "pedas",
                status: "active"
            },
            {
                id: 2,
                name: "crispy melt deluxe",
                price: 13000,
                image: "foto/crispy melt deluxe.jpg",
                description: "Kesan: garing di luar, lembut & creamy di dalam.",
                details: "Kesan: garing di luar, lembut & creamy di dalam.",
                category: "original",
                status: "active"
            },
            {
                id: 3,
                name: "Golden chili crunch",
                price: 15000,
                image: "foto/Golden chili crunch.jpg",
                description: "Kesan: renyah, gurih dengan sentuhan manis-pedas saus khas.",
                details: "Kesan: renyah, gurih dengan sentuhan manis-pedas saus khas.",
                category: "pedas",
                status: "active"
            },
            {
                id: 4,
                name: "bila bila ayam pangsit",
                price: 10000,
                image: "foto/bils bila ayam pangsit.jpg",
                description: "Isi ayam lembut dengan bumbu bawang, merica, dan sedikit sayuran—rasa gurih klasik seperti pangsit ayam pada umumnya.",
                details: "Isi ayam lembut dengan bumbu bawang, merica, dan sedikit sayuran—rasa gurih klasik seperti pangsit ayam pada umumnya.",
                category: "ayam isi 4",
                status: "active"
            },
            {
                id: 5,
                name: "pangsit kuah mercon",
                price: 20000,
                image: "foto/pangsit kuah mercon.jpg",
                description: "Cocok untuk pangsit kuah. Menggunakan cabai rawit, sambal mercon, dan bumbu pedas gurih.",
                details: "Cocok untuk pangsit kuah. Menggunakan cabai rawit, sambal mercon, dan bumbu pedas gurih.",
                category: "pedas",
                status: "active"
            },
            {
                id: 6,
                name: "pangsit isi tahu",
                price: 15000,
                image: "foto/pangsit isi tahu.jpg",
                description: "Pangsit goreng dengan isian udang utuh yang segar.",
                details: "Setiap pangsit berisi udang utuh pilihan dengan bumbu spesial. Sangat cocok untuk pecinta seafood.",
                category: "udang",
                status: "active"
            }
        ];
        
        // Data pesanan dari toko utama
        let customerOrders = JSON.parse(localStorage.getItem('customerOrders')) || [];
        
        // Pengaturan toko
        let storeSettings = JSON.parse(localStorage.getItem('storeSettings')) || {
            storeName: "PANGS!T Store",
            storeEmail: "sitirusmi54@gmail.com",
            storePhone: "+62 831-9524-3139",
            storeAddress: "Jl.panongan desa panongan kec panongan kabupaten tangerang",
            shippingFee: 15000
        };
        
        // Status admin login
        let isAdminLoggedIn = localStorage.getItem('adminLoggedIn') === 'true';
        
        // DOM Elements
        const loginPage = document.getElementById('loginPage');
        const adminDashboard = document.getElementById('adminDashboard');
        const loginForm = document.getElementById('loginForm');
        const logoutBtn = document.getElementById('logoutBtn');
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const sidebar = document.getElementById('sidebar');
        const pageTitle = document.getElementById('pageTitle');
        const searchInput = document.getElementById('searchInput');
        const adminInitial = document.getElementById('adminInitial');
        const pendingCount = document.getElementById('pendingCount');
        
        // Halaman
        const pages = {
            dashboard: document.getElementById('dashboardPage'),
            orders: document.getElementById('ordersPage'),
            products: document.getElementById('productsPage'),
            customers: document.getElementById('customersPage'),
            reports: document.getElementById('reportsPage'),
            settings: document.getElementById('settingsPage')
        };
        
        // Menu items
        const menuItems = document.querySelectorAll('.menu-item');
        
        // ==================== FUNGSI UTILITAS ====================
        
        // Format Rupiah
        function formatRupiah(amount) {
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(amount);
        }
        
        // Format tanggal
        function formatDate(dateString) {
            const date = new Date(dateString);
            return date.toLocaleDateString('id-ID', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            });
        }
        
        // Tampilkan notifikasi
        function showAlert(message, type = 'success') {
            // Hapus alert sebelumnya
            const existingAlert = document.querySelector('.alert');
            if (existingAlert) {
                existingAlert.remove();
            }
            
            // Buat alert baru
            const alert = document.createElement('div');
            alert.className = `alert alert-${type === 'success' ? 'success' : 'error'}`;
            alert.innerHTML = `
                <div>${message}</div>
                <button class="close-alert">&times;</button>
            `;
            
            // Tambahkan ke content
            const content = document.querySelector('.content');
            content.insertBefore(alert, content.firstChild);
            
            // Auto hide setelah 5 detik
            setTimeout(() => {
                if (alert.parentNode) {
                    alert.remove();
                }
            }, 5000);
            
            // Event listener untuk tombol close
            alert.querySelector('.close-alert').addEventListener('click', () => {
                alert.remove();
            });
        }
        
        // Hitung statistik pesanan
        function calculateOrderStats() {
            const totalOrders = customerOrders.length;
            const pendingOrders = customerOrders.filter(order => order.status === 'processing').length;
            const totalRevenue = customerOrders.reduce((sum, order) => sum + order.total, 0);
            
            // Hitung pelanggan unik
            const uniqueCustomers = new Set(customerOrders.map(order => order.customer.email)).size;
            
            return {
                totalOrders,
                pendingOrders,
                totalRevenue,
                uniqueCustomers
            };
        }
        
        // Update dashboard stats
        function updateDashboardStats() {
            const stats = calculateOrderStats();
            
            document.getElementById('totalOrders').textContent = stats.totalOrders;
            document.getElementById('pendingOrders').textContent = stats.pendingOrders;
            document.getElementById('totalRevenue').textContent = formatRupiah(stats.totalRevenue);
            document.getElementById('totalCustomers').textContent = stats.uniqueCustomers;
            
            // Update badge di menu
            pendingCount.textContent = stats.pendingOrders;
        }
        
        // Render pesanan terbaru
        function renderRecentOrders() {
            const table = document.getElementById('recentOrdersTable');
            const recentOrders = customerOrders.slice(0, 5); // Ambil 5 pesanan terbaru
            
            if (recentOrders.length === 0) {
                table.innerHTML = `
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 40px;">
                            <i class="fas fa-box-open" style="font-size: 48px; color: var(--light-gray); margin-bottom: 15px; display: block;"></i>
                            <p style="color: var(--gray);">Belum ada pesanan</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            table.innerHTML = '';
            
            recentOrders.forEach(order => {
                const row = document.createElement('tr');
                
                // Tentukan kelas status
                let statusClass = 'status-lunas';
                let statusText = 'LUNAS';
                
                if (order.status === 'processing') {
                    statusClass = 'status-processing';
                    statusText = 'Diproses';
                } else if (order.status === 'shipped') {
                    statusClass = 'status-shipped';
                    statusText = 'Dikirim';
                } else if (order.status === 'delivered') {
                    statusClass = 'status-delivered';
                    statusText = 'Sampai';
                } else if (order.status === 'cancelled') {
                    statusClass = 'status-cancelled';
                    statusText = 'Batal';
                }
                
                row.innerHTML = `
                    <td><strong>${order.id}</strong></td>
                    <td>${order.date}</td>
                    <td>${order.customer.name}</td>
                    <td>${formatRupiah(order.total)}</td>
                    <td><span class="status-badge ${statusClass}">${statusText}</span></td>
                    <td>
                        <button class="btn btn-sm btn-outline view-order-btn" data-id="${order.id}">
                            <i class="fas fa-eye"></i> Lihat
                        </button>
                        ${order.status === 'processing' ? `
                            <button class="btn btn-sm btn-success update-status-btn" data-id="${order.id}" data-status="shipped">
                                <i class="fas fa-truck"></i> Kirim
                            </button>
                        ` : ''}
                    </td>
                `;
                
                table.appendChild(row);
            });
            
            // Tambahkan event listener untuk tombol
            document.querySelectorAll('.view-order-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    showOrderDetail(orderId);
                });
            });
            
            document.querySelectorAll('.update-status-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    const newStatus = this.getAttribute('data-status');
                    updateOrderStatus(orderId, newStatus);
                });
            });
        }
        
        // Render semua pesanan
        function renderAllOrders(filteredOrders = null) {
            const table = document.getElementById('ordersTable');
            const ordersToRender = filteredOrders || customerOrders;
            
            if (ordersToRender.length === 0) {
                table.innerHTML = `
                    <tr>
                        <td colspan="7" style="text-align: center; padding: 40px;">
                            <i class="fas fa-box-open" style="font-size: 48px; color: var(--light-gray); margin-bottom: 15px; display: block;"></i>
                            <p style="color: var(--gray);">Tidak ada pesanan ditemukan</p>
                        </td>
                    </tr>
                `;
                document.getElementById('ordersCount').textContent = '0';
                return;
            }
            
            document.getElementById('ordersCount').textContent = ordersToRender.length;
            
            table.innerHTML = '';
            
            ordersToRender.forEach(order => {
                const row = document.createElement('tr');
                
                // Tentukan kelas status
                let statusClass = 'status-lunas';
                let statusText = 'LUNAS';
                
                if (order.status === 'processing') {
                    statusClass = 'status-processing';
                    statusText = 'Diproses';
                } else if (order.status === 'shipped') {
                    statusClass = 'status-shipped';
                    statusText = 'Dikirim';
                } else if (order.status === 'delivered') {
                    statusClass = 'status-delivered';
                    statusText = 'Sampai';
                } else if (order.status === 'cancelled') {
                    statusClass = 'status-cancelled';
                    statusText = 'Batal';
                }
                
                row.innerHTML = `
                    <td><strong>${order.id}</strong></td>
                    <td>${order.date}<br><small>${order.time}</small></td>
                    <td>
                        <strong>${order.customer.name}</strong><br>
                        <small>${order.customer.phone}</small>
                    </td>
                    <td>${order.paymentMethod.toUpperCase()}</td>
                    <td>${formatRupiah(order.total)}</td>
                    <td><span class="status-badge ${statusClass}">${statusText}</span></td>
                    <td>
                        <button class="btn btn-sm btn-outline view-order-btn" data-id="${order.id}" title="Lihat Detail">
                            <i class="fas fa-eye"></i>
                        </button>
                        <button class="btn btn-sm btn-success update-status-btn" data-id="${order.id}" data-status="processing" ${order.status === 'processing' || order.status === 'lunas' ? '' : 'disabled'} title="Proses Pesanan">
                            <i class="fas fa-cogs"></i>
                        </button>
                        <button class="btn btn-sm btn-warning update-status-btn" data-id="${order.id}" data-status="shipped" ${order.status === 'processing' ? '' : 'disabled'} title="Kirim Pesanan">
                            <i class="fas fa-truck"></i>
                        </button>
                        <button class="btn btn-sm btn-primary update-status-btn" data-id="${order.id}" data-status="delivered" ${order.status === 'shipped' ? '' : 'disabled'} title="Tandai Sampai">
                            <i class="fas fa-check-circle"></i>
                        </button>
                        <button class="btn btn-sm btn-danger update-status-btn" data-id="${order.id}" data-status="cancelled" ${order.status === 'cancelled' ? 'disabled' : ''} title="Batalkan Pesanan">
                            <i class="fas fa-times"></i>
                        </button>
                    </td>
                `;
                
                table.appendChild(row);
            });
            
            // Tambahkan event listener untuk tombol
            document.querySelectorAll('.view-order-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    showOrderDetail(orderId);
                });
            });
            
            document.querySelectorAll('.update-status-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    const newStatus = this.getAttribute('data-status');
                    updateOrderStatus(orderId, newStatus);
                });
            });
        }
        
        // Tampilkan detail pesanan di modal
        function showOrderDetail(orderId) {
            const order = customerOrders.find(o => o.id === orderId);
            if (!order) return;
            
            const modal = document.getElementById('orderDetailModal');
            const content = document.getElementById('orderDetailContent');
            
            // Tentukan status text
            let statusText = 'LUNAS';
            if (order.status === 'processing') statusText = 'Sedang Diproses';
            else if (order.status === 'shipped') statusText = 'Dalam Pengiriman';
            else if (order.status === 'delivered') statusText = 'Telah Dikirim';
            else if (order.status === 'cancelled') statusText = 'Dibatalkan';
            
            // Buat konten modal
            content.innerHTML = `
                <div class="order-detail-section">
                    <h4 class="order-detail-title">Informasi Pesanan</h4>
                    <div class="order-info-grid">
                        <div>
                            <div class="info-item">
                                <div class="info-label">ID Pesanan</div>
                                <div class="info-value">${order.id}</div>
                            </div>
                            <div class="info-item">
                                <div class="info-label">Tanggal</div>
                                <div class="info-value">${order.date} - ${order.time}</div>
                            </div>
                            <div class="info-item">
                                <div class="info-label">Status</div>
                                <div class="info-value">
                                    <span class="status-badge ${order.status === 'lunas' ? 'status-lunas' : 
                                                               order.status === 'processing' ? 'status-processing' : 
                                                               order.status === 'shipped' ? 'status-shipped' : 
                                                               order.status === 'delivered' ? 'status-delivered' : 
                                                               'status-cancelled'}">
                                        ${statusText}
                                    </span>
                                </div>
                            </div>
                        </div>
                        <div>
                            <div class="info-item">
                                <div class="info-label">Metode Pembayaran</div>
                                <div class="info-value">${order.paymentMethod.toUpperCase()}</div>
                            </div>
                            <div class="info-item">
                                <div class="info-label">Catatan</div>
                                <div class="info-value">${order.notes || 'Tidak ada catatan'}</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="order-detail-section">
                    <h4 class="order-detail-title">Informasi Pelanggan</h4>
                    <div class="order-info-grid">
                        <div>
                            <div class="info-item">
                                <div class="info-label">Nama Lengkap</div>
                                <div class="info-value">${order.customer.name}</div>
                            </div>
                            <div class="info-item">
                                <div class="info-label">Email</div>
                                <div class="info-value">${order.customer.email}</div>
                            </div>
                        </div>
                        <div>
                            <div class="info-item">
                                <div class="info-label">Telepon</div>
                                <div class="info-value">${order.customer.phone}</div>
                            </div>
                            <div class="info-item">
                                <div class="info-label">Alamat Pengiriman</div>
                                <div class="info-value">${order.customer.address}</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="order-detail-section">
                    <h4 class="order-detail-title">Detail Produk</h4>
                    <table class="products-table">
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
                    
                    <div class="order-total">
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
                        <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 20px;">
                            <span>TOTAL:</span>
                            <span class="total-amount">${formatRupiah(order.total)}</span>
                        </div>
                    </div>
                </div>
                
                <div class="status-update-form">
                    <h4>Update Status Pesanan</h4>
                    <div class="status-options">
                        <label class="status-option">
                            <input type="radio" name="orderStatus" value="processing" ${order.status === 'processing' ? 'checked' : ''}>
                            <span>Sedang Diproses</span>
                        </label>
                        <label class="status-option">
                            <input type="radio" name="orderStatus" value="shipped" ${order.status === 'shipped' ? 'checked' : ''}>
                            <span>Dalam Pengiriman</span>
                        </label>
                        <label class="status-option">
                            <input type="radio" name="orderStatus" value="delivered" ${order.status === 'delivered' ? 'checked' : ''}>
                            <span>Telah Dikirim</span>
                        </label>
                        <label class="status-option">
                            <input type="radio" name="orderStatus" value="cancelled" ${order.status === 'cancelled' ? 'checked' : ''}>
                            <span>Dibatalkan</span>
                        </label>
                    </div>
                    <div style="display: flex; gap: 10px; margin-top: 20px;">
                        <button class="btn btn-primary" id="updateStatusBtn" data-id="${order.id}">
                            <i class="fas fa-save"></i> Update Status
                        </button>
                        <button class="btn btn-outline" id="printInvoiceBtn" data-id="${order.id}">
                            <i class="fas fa-print"></i> Cetak Invoice
                        </button>
                    </div>
                </div>
            `;
            
            // Tampilkan modal
            modal.classList.add('active');
            
            // Event listener untuk update status
            document.getElementById('updateStatusBtn').addEventListener('click', function() {
                const orderId = this.getAttribute('data-id');
                const selectedStatus = document.querySelector('input[name="orderStatus"]:checked').value;
                updateOrderStatus(orderId, selectedStatus);
                modal.classList.remove('active');
            });
            
            // Event listener untuk cetak invoice
            document.getElementById('printInvoiceBtn').addEventListener('click', function() {
                const orderId = this.getAttribute('data-id');
                printOrderInvoice(orderId);
            });
        }
        
        // Update status pesanan
        function updateOrderStatus(orderId, newStatus) {
            const orderIndex = customerOrders.findIndex(o => o.id === orderId);
            
            if (orderIndex === -1) {
                showAlert('Pesanan tidak ditemukan', 'error');
                return;
            }
            
            // Update status pesanan
            customerOrders[orderIndex].status = newStatus;
            
            // Simpan ke localStorage
            localStorage.setItem('customerOrders', JSON.stringify(customerOrders));
            
            // Update UI
            updateDashboardStats();
            renderRecentOrders();
            renderAllOrders();
            
            // Tampilkan notifikasi
            const statusText = newStatus === 'processing' ? 'Sedang Diproses' :
                             newStatus === 'shipped' ? 'Dalam Pengiriman' :
                             newStatus === 'delivered' ? 'Telah Dikirim' :
                             newStatus === 'cancelled' ? 'Dibatalkan' : 'LUNAS';
            
            showAlert(`Status pesanan ${orderId} berhasil diubah menjadi: ${statusText}`);
        }
        
        // Cetak invoice pesanan
        function printOrderInvoice(orderId) {
            const order = customerOrders.find(o => o.id === orderId);
            if (!order) return;
            
            // Buka window baru untuk cetak
            const printWindow = window.open('', '_blank');
            
            // Konten HTML untuk invoice
            const invoiceHTML = `
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Invoice ${order.id}</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; }
                        .invoice-container { max-width: 800px; margin: 0 auto; }
                        .invoice-header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #ff6b35; padding-bottom: 20px; }
                        .invoice-logo { font-size: 28px; font-weight: bold; color: #ff6b35; margin-bottom: 10px; }
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
                        
                        <div style="display: flex; justify-content: space-between; margin-bottom: 30px;">
                            <div>
                                <h4>Informasi Pesanan</h4>
                                <p><strong>Invoice No:</strong> ${order.id}</p>
                                <p><strong>Tanggal:</strong> ${order.date}</p>
                                <p><strong>Waktu:</strong> ${order.time}</p>
                                <p><strong>Status:</strong> ${order.status === 'lunas' ? 'LUNAS' : 
                                                           order.status === 'processing' ? 'Sedang Diproses' :
                                                           order.status === 'shipped' ? 'Dalam Pengiriman' :
                                                           order.status === 'delivered' ? 'Telah Dikirim' : 'Dibatalkan'}</p>
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
                                        <td>${formatRupiah(product.price)}</td>
                                        <td>${product.quantity}</td>
                                        <td>${formatRupiah(product.price * product.quantity)}</td>
                                    </tr>
                                `).join('')}
                            </tbody>
                        </table>
                        
                        <div class="invoice-totals">
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
                            <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 20px; border-top: 2px solid #ff6b35; padding-top: 10px; margin-top: 10px;">
                                <span>TOTAL:</span>
                                <span style="color: #ff6b35;">${formatRupiah(order.total)}</span>
                            </div>
                        </div>
                        <div style="clear: both;"></div>
                        
                        <div style="margin-top: 30px; padding: 15px; background-color: #f8f9fa; border-radius: 5px;">
                            <p><strong>Metode Pembayaran:</strong> ${order.paymentMethod.toUpperCase()}</p>
                            <p><strong>Catatan:</strong> ${order.notes || 'Tidak ada catatan'}</p>
                            <p style="margin-top: 15px;">Terima kasih telah berbelanja di PANGS!T STORE</p>
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
        
        // Render produk
        function renderProducts() {
            const table = document.getElementById('productsTable');
            const activeProducts = products.filter(p => p.status === 'active');
            
            document.getElementById('productsCount').textContent = activeProducts.length;
            
            if (activeProducts.length === 0) {
                table.innerHTML = `
                    <tr>
                        <td colspan="7" style="text-align: center; padding: 40px;">
                            <i class="fas fa-box-open" style="font-size: 48px; color: var(--light-gray); margin-bottom: 15px; display: block;"></i>
                            <p style="color: var(--gray);">Belum ada produk</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            table.innerHTML = '';
            
            activeProducts.forEach(product => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${product.id}</td>
                    <td>
                        <img src="${product.image}" alt="${product.name}" style="width: 50px; height: 50px; object-fit: cover; border-radius: 5px;" onerror="this.src='https://via.placeholder.com/50x50/e9ecef/6c757d?text=Produk'">
                    </td>
                    <td>
                        <strong>${product.name}</strong><br>
                        <small style="color: var(--gray);">${product.description.substring(0, 50)}...</small>
                    </td>
                    <td>${formatRupiah(product.price)}</td>
                    <td>${product.category}</td>
                    <td>
                        <span class="status-badge ${product.status === 'active' ? 'status-lunas' : 'status-cancelled'}">
                            ${product.status === 'active' ? 'Aktif' : 'Nonaktif'}
                        </span>
                    </td>
                    <td>
                        <button class="btn btn-sm btn-outline edit-product-btn" data-id="${product.id}">
                            <i class="fas fa-edit"></i>
                        </button>
                        <button class="btn btn-sm btn-danger delete-product-btn" data-id="${product.id}">
                            <i class="fas fa-trash"></i>
                        </button>
                    </td>
                `;
                
                table.appendChild(row);
            });
            
            // Event listener untuk tombol edit
            document.querySelectorAll('.edit-product-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    editProduct(productId);
                });
            });
            
            // Event listener untuk tombol delete
            document.querySelectorAll('.delete-product-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    const productId = parseInt(this.getAttribute('data-id'));
                    deleteProduct(productId);
                });
            });
        }
        
        // Tambah/edit produk
        function editProduct(productId = null) {
            const modal = document.getElementById('productModal');
            const title = document.getElementById('productModalTitle');
            const form = document.getElementById('productForm');
            
            if (productId) {
                // Mode edit
                title.textContent = 'Edit Produk';
                const product = products.find(p => p.id === productId);
                
                if (product) {
                    document.getElementById('productId').value = product.id;
                    document.getElementById('productName').value = product.name;
                    document.getElementById('productPrice').value = product.price;
                    document.getElementById('productCategory').value = product.category;
                    document.getElementById('productDescription').value = product.description;
                    document.getElementById('productImage').value = product.image;
                    document.getElementById('productDetails').value = product.details;
                    document.getElementById('productStatus').value = product.status;
                }
            } else {
                // Mode tambah
                title.textContent = 'Tambah Produk Baru';
                form.reset();
                document.getElementById('productId').value = '';
                document.getElementById('productStatus').value = 'active';
            }
            
            modal.classList.add('active');
        }
        
        // Hapus produk
        function deleteProduct(productId) {
            if (!confirm('Apakah Anda yakin ingin menghapus produk ini?')) {
                return;
            }
            
            const productIndex = products.findIndex(p => p.id === productId);
            
            if (productIndex !== -1) {
                // Soft delete (ubah status menjadi inactive)
                products[productIndex].status = 'inactive';
                
                // Simpan ke localStorage
                localStorage.setItem('products', JSON.stringify(products));
                
                // Update UI
                renderProducts();
                showAlert('Produk berhasil dihapus');
            }
        }
        
        // Render data pelanggan
        function renderCustomers() {
            const table = document.getElementById('customersTable');
            
            // Hitung statistik pelanggan
            const customerMap = new Map();
            
            customerOrders.forEach(order => {
                const email = order.customer.email;
                const name = order.customer.name;
                const phone = order.customer.phone;
                
                if (!customerMap.has(email)) {
                    customerMap.set(email, {
                        name: name,
                        email: email,
                        phone: phone,
                        totalOrders: 0,
                        totalSpent: 0,
                        lastOrder: ''
                    });
                }
                
                const customer = customerMap.get(email);
                customer.totalOrders += 1;
                customer.totalSpent += order.total;
                
                // Cari tanggal terakhir pesanan
                const orderDate = `${order.date} ${order.time}`;
                if (!customer.lastOrder || orderDate > customer.lastOrder) {
                    customer.lastOrder = orderDate;
                }
            });
            
            const customers = Array.from(customerMap.values());
            
            document.getElementById('customersCount').textContent = customers.length;
            
            if (customers.length === 0) {
                table.innerHTML = `
                    <tr>
                        <td colspan="6" style="text-align: center; padding: 40px;">
                            <i class="fas fa-users" style="font-size: 48px; color: var(--light-gray); margin-bottom: 15px; display: block;"></i>
                            <p style="color: var(--gray);">Belum ada data pelanggan</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            table.innerHTML = '';
            
            customers.forEach(customer => {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${customer.name}</td>
                    <td>${customer.email}</td>
                    <td>${customer.phone}</td>
                    <td>${customer.totalOrders}</td>
                    <td>${formatRupiah(customer.totalSpent)}</td>
                    <td>${customer.lastOrder}</td>
                `;
                
                table.appendChild(row);
            });
        }
        
        // Render laporan
        function renderReports() {
            // Untuk demo, tampilkan statistik bulan ini
            const now = new Date();
            const currentMonth = now.getMonth() + 1;
            const currentYear = now.getFullYear();
            
            // Filter pesanan bulan ini
            const monthlyOrders = customerOrders.filter(order => {
                const orderDate = new Date(order.timestamp || Date.now());
                return orderDate.getMonth() + 1 === currentMonth && 
                       orderDate.getFullYear() === currentYear;
            });
            
            // Hitung statistik
            const reportTransactions = monthlyOrders.length;
            const reportRevenue = monthlyOrders.reduce((sum, order) => sum + order.total, 0);
            
            // Hitung total produk terjual
            let reportProductsSold = 0;
            monthlyOrders.forEach(order => {
                order.products.forEach(product => {
                    reportProductsSold += product.quantity;
                });
            });
            
            // Hitung rata-rata pesanan
            const reportAvgOrder = reportTransactions > 0 ? reportRevenue / reportTransactions : 0;
            
            // Update UI
            document.getElementById('reportTransactions').textContent = reportTransactions;
            document.getElementById('reportRevenue').textContent = formatRupiah(reportRevenue);
            document.getElementById('reportProductsSold').textContent = reportProductsSold;
            document.getElementById('reportAvgOrder').textContent = formatRupiah(reportAvgOrder);
            
            // Hitung produk terlaris
            const productSales = new Map();
            
            monthlyOrders.forEach(order => {
                order.products.forEach(product => {
                    const productId = product.name;
                    if (!productSales.has(productId)) {
                        productSales.set(productId, {
                            name: product.name,
                            quantity: 0,
                            revenue: 0
                        });
                    }
                    
                    const sales = productSales.get(productId);
                    sales.quantity += product.quantity;
                    sales.revenue += product.price * product.quantity;
                });
            });
            
            // Urutkan berdasarkan quantity terjual
            const topProducts = Array.from(productSales.values())
                .sort((a, b) => b.quantity - a.quantity)
                .slice(0, 5); // Ambil 5 teratas
            
            // Render tabel produk terlaris
            const table = document.getElementById('topProductsTable');
            
            if (topProducts.length === 0) {
                table.innerHTML = `
                    <tr>
                        <td colspan="4" style="text-align: center; padding: 40px;">
                            <i class="fas fa-chart-line" style="font-size: 48px; color: var(--light-gray); margin-bottom: 15px; display: block;"></i>
                            <p style="color: var(--gray);">Belum ada data penjualan</p>
                        </td>
                    </tr>
                `;
                return;
            }
            
            table.innerHTML = '';
            
            // Hitung total revenue untuk persentase
            const totalRevenue = topProducts.reduce((sum, product) => sum + product.revenue, 0);
            
            topProducts.forEach(product => {
                const percentage = totalRevenue > 0 ? (product.revenue / totalRevenue * 100).toFixed(1) : 0;
                
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${product.name}</td>
                    <td>${product.quantity}</td>
                    <td>${formatRupiah(product.revenue)}</td>
                    <td>
                        <div style="display: flex; align-items: center; gap: 10px;">
                            <span>${percentage}%</span>
                            <div style="flex: 1; height: 10px; background-color: var(--light-gray); border-radius: 5px; overflow: hidden;">
                                <div style="width: ${percentage}%; height: 100%; background-color: var(--primary);"></div>
                            </div>
                        </div>
                    </td>
                `;
                
                table.appendChild(row);
            });
        }
        
        // Load pengaturan
        function loadSettings() {
            document.getElementById('storeName').value = storeSettings.storeName;
            document.getElementById('storeEmail').value = storeSettings.storeEmail;
            document.getElementById('storePhone').value = storeSettings.storePhone;
            document.getElementById('storeAddress').value = storeSettings.storeAddress;
            document.getElementById('shippingFee').value = storeSettings.shippingFee;
        }
        
        // ==================== EVENT LISTENERS ====================
        
        // Login
        loginForm.addEventListener('submit', function(e) {
            e.preventDefault();
            
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            
            if (username === adminCredentials.username && password === adminCredentials.password) {
                // Login berhasil
                isAdminLoggedIn = true;
                localStorage.setItem('adminLoggedIn', 'true');
                
                // Tampilkan dashboard admin
                loginPage.style.display = 'none';
                adminDashboard.style.display = 'flex';
                
                // Inisialisasi dashboard
                initializeDashboard();
                
                showAlert('Login berhasil! Selamat datang di dashboard admin.');
            } else {
                alert('Username atau password salah!');
            }
        });
        
        // Logout
        logoutBtn.addEventListener('click', function() {
            if (confirm('Apakah Anda yakin ingin logout?')) {
                isAdminLoggedIn = false;
                localStorage.setItem('adminLoggedIn', 'false');
                
                // Kembali ke halaman login
                adminDashboard.style.display = 'none';
                loginPage.style.display = 'flex';
                
                // Reset form login
                loginForm.reset();
            }
        });
        
        // Menu mobile toggle
        mobileMenuBtn.addEventListener('click', function() {
            sidebar.classList.toggle('active');
        });
        
        // Navigasi halaman
        menuItems.forEach(item => {
            item.addEventListener('click', function(e) {
                e.preventDefault();
                
                // Dapatkan halaman yang dipilih
                const page = this.getAttribute('data-page');
                
                // Update menu aktif
                menuItems.forEach(i => i.classList.remove('active'));
                this.classList.add('active');
                
                // Sembunyikan semua halaman
                Object.values(pages).forEach(p => p.style.display = 'none');
                
                // Tampilkan halaman yang dipilih
                pages[page].style.display = 'block';
                
                // Update judul halaman
                const pageTitles = {
                    dashboard: 'Dashboard',
                    orders: 'Kelola Pesanan',
                    products: 'Kelola Produk',
                    customers: 'Data Pelanggan',
                    reports: 'Laporan Penjualan',
                    settings: 'Pengaturan Sistem'
                };
                
                pageTitle.textContent = pageTitles[page];
                
                // Tutup sidebar di mobile
                if (window.innerWidth <= 992) {
                    sidebar.classList.remove('active');
                }
                
                // Load data halaman yang dipilih
                switch(page) {
                    case 'dashboard':
                        updateDashboardStats();
                        renderRecentOrders();
                        break;
                    case 'orders':
                        renderAllOrders();
                        break;
                    case 'products':
                        renderProducts();
                        break;
                    case 'customers':
                        renderCustomers();
                        break;
                    case 'reports':
                        renderReports();
                        break;
                    case 'settings':
                        loadSettings();
                        break;
                }
            });
        });
        
        // Search pesanan
        searchInput.addEventListener('input', function() {
            const searchTerm = this.value.toLowerCase().trim();
            
            if (searchTerm === '') {
                renderAllOrders();
                return;
            }
            
            const filteredOrders = customerOrders.filter(order => {
                return (
                    order.id.toLowerCase().includes(searchTerm) ||
                    order.customer.name.toLowerCase().includes(searchTerm) ||
                    order.customer.email.toLowerCase().includes(searchTerm) ||
                    order.customer.phone.includes(searchTerm)
                );
            });
            
            renderAllOrders(filteredOrders);
        });
        
        // Filter pesanan
        document.getElementById('applyFilter').addEventListener('click', function() {
            const statusFilter = document.getElementById('filterStatus').value;
            const startDate = document.getElementById('filterStartDate').value;
            const endDate = document.getElementById('filterEndDate').value;
            
            let filteredOrders = customerOrders;
            
            // Filter berdasarkan status
            if (statusFilter !== 'all') {
                filteredOrders = filteredOrders.filter(order => order.status === statusFilter);
            }
            
            // Filter berdasarkan tanggal
            if (startDate) {
                const start = new Date(startDate);
                filteredOrders = filteredOrders.filter(order => {
                    const orderDate = new Date(order.timestamp || Date.now());
                    return orderDate >= start;
                });
            }
            
            if (endDate) {
                const end = new Date(endDate);
                end.setHours(23, 59, 59, 999); // Akhir hari
                filteredOrders = filteredOrders.filter(order => {
                    const orderDate = new Date(order.timestamp || Date.now());
                    return orderDate <= end;
                });
            }
            
            renderAllOrders(filteredOrders);
        });
        
        // Refresh data
        document.getElementById('refreshData').addEventListener('click', function() {
            // Reload data dari localStorage
            customerOrders = JSON.parse(localStorage.getItem('customerOrders')) || [];
            products = JSON.parse(localStorage.getItem('products')) || products;
            
            updateDashboardStats();
            renderRecentOrders();
            showAlert('Data berhasil diperbarui');
        });
        
        // View all orders
        document.getElementById('viewAllOrders').addEventListener('click', function() {
            // Navigasi ke halaman orders
            document.querySelector('.menu-item[data-page="orders"]').click();
        });
        
        // Export orders
        document.getElementById('exportOrders').addEventListener('click', function() {
            // Buat data CSV
            let csvContent = "ID Pesanan,Tanggal,Pelanggan,Email,Telepon,Total,Status,Metode Bayar\n";
            
            customerOrders.forEach(order => {
                const row = [
                    order.id,
                    order.date,
                    order.customer.name,
                    order.customer.email,
                    order.customer.phone,
                    order.total,
                    order.status,
                    order.paymentMethod
                ];
                
                csvContent += row.join(",") + "\n";
            });
            
            // Buat blob dan download
            const blob = new Blob([csvContent], { type: 'text/csv' });
            const url = window.URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `orders_${new Date().toISOString().split('T')[0]}.csv`;
            a.click();
            
            showAlert('Data pesanan berhasil diexport');
        });
        
        // Tambah produk
        document.getElementById('addProductBtn').addEventListener('click', function() {
            editProduct(); // Mode tambah
        });
        
        // Simpan produk
        document.getElementById('productForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const productId = document.getElementById('productId').value;
            const productName = document.getElementById('productName').value;
            const productPrice = parseInt(document.getElementById('productPrice').value);
            const productCategory = document.getElementById('productCategory').value;
            const productDescription = document.getElementById('productDescription').value;
            const productImage = document.getElementById('productImage').value;
            const productDetails = document.getElementById('productDetails').value;
            const productStatus = document.getElementById('productStatus').value;
            
            if (productId) {
                // Mode edit
                const index = products.findIndex(p => p.id === parseInt(productId));
                if (index !== -1) {
                    products[index] = {
                        ...products[index],
                        name: productName,
                        price: productPrice,
                        category: productCategory,
                        description: productDescription,
                        image: productImage,
                        details: productDetails,
                        status: productStatus
                    };
                }
            } else {
                // Mode tambah
                const newId = products.length > 0 ? Math.max(...products.map(p => p.id)) + 1 : 1;
                products.push({
                    id: newId,
                    name: productName,
                    price: productPrice,
                    image: productImage,
                    description: productDescription,
                    details: productDetails,
                    category: productCategory,
                    status: productStatus
                });
            }
            
            // Simpan ke localStorage
            localStorage.setItem('products', JSON.stringify(products));
            
            // Update UI
            renderProducts();
            
            // Tutup modal
            document.getElementById('productModal').classList.remove('active');
            
            // Tampilkan notifikasi
            showAlert(`Produk ${productName} berhasil disimpan`);
        });
        
        // Batal simpan produk
        document.getElementById('cancelProduct').addEventListener('click', function() {
            document.getElementById('productModal').classList.remove('active');
        });
        
        // Generate report
        document.getElementById('generateReport').addEventListener('click', function() {
            // Buat laporan PDF sederhana (untuk demo)
            const reportWindow = window.open('', '_blank');
            
            const reportHTML = `
                <!DOCTYPE html>
                <html>
                <head>
                    <title>Laporan Penjualan PANGS!T</title>
                    <style>
                        body { font-family: Arial, sans-serif; margin: 20px; }
                        .report-header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #2d3047; padding-bottom: 20px; }
                        .report-title { font-size: 24px; font-weight: bold; color: #2d3047; }
                        .report-period { color: #6c757d; }
                        .stats-grid { display: grid; grid-template-columns: repeat(4, 1fr); gap: 20px; margin: 30px 0; }
                        .stat-box { text-align: center; padding: 20px; border: 1px solid #e9ecef; border-radius: 5px; }
                        .stat-value { font-size: 24px; font-weight: bold; color: #ff6b35; margin: 10px 0; }
                        .stat-label { color: #6c757d; font-size: 14px; }
                        table { width: 100%; border-collapse: collapse; margin: 20px 0; }
                        th, td { padding: 10px; border: 1px solid #ddd; text-align: left; }
                        th { background-color: #f8f9fa; }
                    </style>
                </head>
                <body>
                    <div class="report-header">
                        <div class="report-title">Laporan Penjualan PANGS!T Store</div>
                        <div class="report-period">Periode: ${new Date().toLocaleDateString('id-ID', { 
                            day: '2-digit', 
                            month: 'long', 
                            year: 'numeric' 
                        })}</div>
                    </div>
                    
                    <div class="stats-grid">
                        <div class="stat-box">
                            <div class="stat-label">Total Pesanan</div>
                            <div class="stat-value">${customerOrders.length}</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-label">Total Pendapatan</div>
                            <div class="stat-value">${formatRupiah(customerOrders.reduce((sum, order) => sum + order.total, 0))}</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-label">Pelanggan</div>
                            <div class="stat-value">${new Set(customerOrders.map(order => order.customer.email)).size}</div>
                        </div>
                        <div class="stat-box">
                            <div class="stat-label">Rata-rata Pesanan</div>
                            <div class="stat-value">${formatRupiah(customerOrders.length > 0 ? 
                                customerOrders.reduce((sum, order) => sum + order.total, 0) / customerOrders.length : 0)}</div>
                        </div>
                    </div>
                    
                    <h3>Pesanan Terbaru</h3>
                    <table>
                        <thead>
                            <tr>
                                <th>ID Pesanan</th>
                                <th>Tanggal</th>
                                <th>Pelanggan</th>
                                <th>Total</th>
                                <th>Status</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${customerOrders.slice(0, 10).map(order => `
                                <tr>
                                    <td>${order.id}</td>
                                    <td>${order.date}</td>
                                    <td>${order.customer.name}</td>
                                    <td>${formatRupiah(order.total)}</td>
                                    <td>${order.status}</td>
                                </tr>
                            `).join('')}
                        </tbody>
                    </table>
                    
                    <div style="text-align: center; margin-top: 40px; color: #6c757d; font-size: 14px;">
                        <p>Laporan ini dibuat otomatis oleh sistem PANGS!T Admin</p>
                        <p>${new Date().toLocaleString('id-ID')}</p>
                    </div>
                    
                    <script>
                        window.onload = function() {
                            window.print();
                        }
                    <\/script>
                </body>
                </html>
            `;
            
            reportWindow.document.write(reportHTML);
            reportWindow.document.close();
        });
        
        // Apply report filter
        document.getElementById('applyReportFilter').addEventListener('click', function() {
            renderReports();
            showAlert('Filter laporan diterapkan');
        });
        
        // Toggle custom date range
        document.getElementById('reportPeriod').addEventListener('change', function() {
            const customDateRange = document.getElementById('customDateRange');
            if (this.value === 'custom') {
                customDateRange.style.display = 'block';
            } else {
                customDateRange.style.display = 'none';
            }
        });
        
        // Simpan pengaturan toko
        document.getElementById('storeSettingsForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            storeSettings = {
                storeName: document.getElementById('storeName').value,
                storeEmail: document.getElementById('storeEmail').value,
                storePhone: document.getElementById('storePhone').value,
                storeAddress: document.getElementById('storeAddress').value,
                shippingFee: parseInt(document.getElementById('shippingFee').value)
            };
            
            // Simpan ke localStorage
            localStorage.setItem('storeSettings', JSON.stringify(storeSettings));
            
            showAlert('Pengaturan toko berhasil disimpan');
        });
        
        // Update password admin
        document.getElementById('adminAccountForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const newPassword = document.getElementById('adminPassword').value;
            const confirmPassword = document.getElementById('adminConfirmPassword').value;
            
            if (newPassword && newPassword !== confirmPassword) {
                alert('Password tidak cocok!');
                return;
            }
            
            if (newPassword) {
                adminCredentials.password = newPassword;
                showAlert('Password admin berhasil diperbarui');
            } else {
                showAlert('Tidak ada perubahan password');
            }
            
            // Reset form
            document.getElementById('adminPassword').value = '';
            document.getElementById('adminConfirmPassword').value = '';
        });
        
        // Close modal
        document.getElementById('closeOrderModal').addEventListener('click', function() {
            document.getElementById('orderDetailModal').classList.remove('active');
        });
        
        document.getElementById('closeProductModal').addEventListener('click', function() {
            document.getElementById('productModal').classList.remove('active');
        });
        
        // Close modal ketika klik di luar
        document.querySelectorAll('.modal').forEach(modal => {
            modal.addEventListener('click', function(e) {
                if (e.target === this) {
                    this.classList.remove('active');
                }
            });
        });
        
        // ==================== INISIALISASI ====================
        
        function initializeDashboard() {
            // Set initial admin initial
            adminInitial.textContent = adminCredentials.username.charAt(0).toUpperCase();
            
            // Load data dari localStorage
            customerOrders = JSON.parse(localStorage.getItem('customerOrders')) || [];
            products = JSON.parse(localStorage.getItem('products')) || products;
            storeSettings = JSON.parse(localStorage.getItem('storeSettings')) || storeSettings;
            
            // Tampilkan dashboard default
            updateDashboardStats();
            renderRecentOrders();
            
            // Set judul halaman default
            pageTitle.textContent = 'Dashboard';
            
            console.log('✅ Admin PANGS!T siap digunakan');
        }
        
        // Cek status login saat halaman dimuat
        document.addEventListener('DOMContentLoaded', function() {
            if (isAdminLoggedIn) {
                loginPage.style.display = 'none';
                adminDashboard.style.display = 'flex';
                initializeDashboard();
            } else {
                loginPage.style.display = 'flex';
                adminDashboard.style.display = 'none';
            }
        });
    </script>
</body>
</html>
