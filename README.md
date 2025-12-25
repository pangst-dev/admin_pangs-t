<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin PANGS!T - Dashboard Pesanan</title>
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
            overflow-x: hidden;
        }
        
        .container {
            width: 100%;
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header Admin */
        .admin-header {
            background-color: var(--secondary);
            color: white;
            padding: 20px 0;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .admin-nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .admin-logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .admin-logo-icon {
            color: var(--primary);
            font-size: 28px;
        }
        
        .admin-logo-text {
            font-size: 24px;
            font-weight: 700;
        }
        
        .admin-logo-text span {
            color: var(--primary);
        }
        
        .admin-controls {
            display: flex;
            align-items: center;
            gap: 20px;
        }
        
        .refresh-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 50%;
            width: 40px;
            height: 40px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .refresh-btn:hover {
            background-color: var(--primary-dark);
            transform: rotate(90deg);
        }
        
        .admin-status {
            display: flex;
            align-items: center;
            gap: 10px;
            background-color: rgba(255, 255, 255, 0.1);
            padding: 8px 15px;
            border-radius: 50px;
        }
        
        .status-indicator {
            width: 10px;
            height: 10px;
            background-color: var(--success);
            border-radius: 50%;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.5; }
            100% { opacity: 1; }
        }
        
        /* Dashboard Stats */
        .dashboard-stats {
            padding: 40px 0;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
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
            color: white;
        }
        
        .stat-icon.pending { background-color: var(--warning); }
        .stat-icon.processing { background-color: var(--info); }
        .stat-icon.completed { background-color: var(--success); }
        .stat-icon.revenue { background-color: var(--primary); }
        
        .stat-info h3 {
            font-size: 14px;
            color: var(--gray);
            margin-bottom: 5px;
            text-transform: uppercase;
            letter-spacing: 1px;
        }
        
        .stat-number {
            font-size: 28px;
            font-weight: 700;
            color: var(--secondary);
        }
        
        /* Filter Controls */
        .filter-section {
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }
        
        .filter-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .filter-header h2 {
            color: var(--secondary);
        }
        
        .filter-controls {
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .filter-group {
            display: flex;
            flex-direction: column;
            gap: 5px;
        }
        
        .filter-group label {
            font-size: 14px;
            color: var(--gray);
            font-weight: 600;
        }
        
        .filter-select, .filter-input {
            padding: 10px 15px;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            min-width: 180px;
            background-color: white;
        }
        
        .filter-select:focus, .filter-input:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        .filter-actions {
            display: flex;
            gap: 10px;
            align-items: flex-end;
        }
        
        .btn-filter {
            padding: 10px 20px;
            background-color: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
        }
        
        .btn-filter:hover {
            background-color: var(--primary-dark);
        }
        
        .btn-reset {
            padding: 10px 20px;
            background-color: var(--light-gray);
            color: var(--dark);
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
        }
        
        .btn-reset:hover {
            background-color: #ddd;
        }
        
        /* Orders Table */
        .orders-section {
            background-color: white;
            border-radius: 10px;
            padding: 0;
            box-shadow: var(--shadow);
            margin-bottom: 40px;
            overflow: hidden;
        }
        
        .orders-header {
            padding: 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .orders-header h2 {
            color: var(--secondary);
        }
        
        .orders-count {
            background-color: var(--light-gray);
            color: var(--dark);
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
        }
        
        .orders-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .orders-table thead {
            background-color: var(--light);
        }
        
        .orders-table th {
            padding: 15px 20px;
            text-align: left;
            font-weight: 600;
            color: var(--secondary);
            border-bottom: 1px solid var(--light-gray);
        }
        
        .orders-table td {
            padding: 15px 20px;
            border-bottom: 1px solid var(--light-gray);
            vertical-align: top;
        }
        
        .order-id {
            font-weight: 600;
            color: var(--secondary);
            font-family: monospace;
        }
        
        .order-customer {
            min-width: 200px;
        }
        
        .customer-name {
            font-weight: 600;
            margin-bottom: 3px;
        }
        
        .customer-phone {
            font-size: 13px;
            color: var(--gray);
        }
        
        .order-items {
            max-width: 250px;
        }
        
        .order-item {
            display: flex;
            justify-content: space-between;
            margin-bottom: 5px;
            font-size: 14px;
        }
        
        .order-item:last-child {
            margin-bottom: 0;
        }
        
        .item-name {
            overflow: hidden;
            text-overflow: ellipsis;
            white-space: nowrap;
            max-width: 150px;
        }
        
        .order-total {
            font-weight: 700;
            color: var(--primary);
        }
        
        .status-badge {
            display: inline-block;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        
        .status-pending {
            background-color: rgba(255, 193, 7, 0.1);
            color: #856404;
        }
        
        .status-processing {
            background-color: rgba(23, 162, 184, 0.1);
            color: #0c5460;
        }
        
        .status-completed {
            background-color: rgba(40, 167, 69, 0.1);
            color: #155724;
        }
        
        .status-cancelled {
            background-color: rgba(220, 53, 69, 0.1);
            color: #721c24;
        }
        
        .action-buttons {
            display: flex;
            gap: 8px;
        }
        
        .btn-action {
            width: 36px;
            height: 36px;
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            border: none;
            cursor: pointer;
            transition: var(--transition);
            font-size: 14px;
        }
        
        .btn-view {
            background-color: rgba(23, 162, 184, 0.1);
            color: var(--info);
        }
        
        .btn-view:hover {
            background-color: var(--info);
            color: white;
        }
        
        .btn-process {
            background-color: rgba(40, 167, 69, 0.1);
            color: var(--success);
        }
        
        .btn-process:hover {
            background-color: var(--success);
            color: white;
        }
        
        .btn-cancel {
            background-color: rgba(220, 53, 69, 0.1);
            color: var(--danger);
        }
        
        .btn-cancel:hover {
            background-color: var(--danger);
            color: white;
        }
        
        .empty-orders {
            padding: 60px 20px;
            text-align: center;
            color: var(--gray);
        }
        
        .empty-icon {
            font-size: 60px;
            color: var(--light-gray);
            margin-bottom: 20px;
        }
        
        /* Order Detail Modal */
        .order-modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .order-modal.active {
            display: flex;
        }
        
        .order-modal-content {
            background-color: white;
            border-radius: 10px;
            max-width: 800px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
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
            padding: 30px 30px 20px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .modal-header h2 {
            color: var(--secondary);
            margin-bottom: 5px;
        }
        
        .modal-order-id {
            color: var(--gray);
            font-family: monospace;
        }
        
        .modal-body {
            padding: 30px;
        }
        
        .modal-section {
            margin-bottom: 30px;
        }
        
        .modal-section h3 {
            color: var(--secondary);
            margin-bottom: 15px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .customer-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
        }
        
        .info-item {
            margin-bottom: 10px;
        }
        
        .info-label {
            font-weight: 600;
            color: var(--gray);
            font-size: 14px;
            margin-bottom: 3px;
        }
        
        .order-items-list {
            background-color: var(--light);
            border-radius: 8px;
            padding: 20px;
        }
        
        .order-item-detail {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid rgba(0, 0, 0, 0.05);
        }
        
        .order-item-detail:last-child {
            border-bottom: none;
        }
        
        .item-image {
            width: 60px;
            height: 60px;
            object-fit: cover;
            border-radius: 8px;
            margin-right: 15px;
        }
        
        .item-info {
            flex: 1;
        }
        
        .item-name {
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .item-price {
            color: var(--primary);
            font-weight: 600;
        }
        
        .order-summary {
            background-color: var(--light);
            border-radius: 8px;
            padding: 20px;
        }
        
        .summary-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 10px;
        }
        
        .summary-row.total {
            font-weight: 700;
            font-size: 18px;
            color: var(--primary);
            margin-top: 10px;
            padding-top: 10px;
            border-top: 2px solid rgba(0, 0, 0, 0.1);
        }
        
        .modal-actions {
            display: flex;
            gap: 15px;
            justify-content: flex-end;
            padding-top: 20px;
            border-top: 1px solid var(--light-gray);
        }
        
        .btn-modal {
            padding: 12px 25px;
            border-radius: 8px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
        }
        
        .btn-mark-processing {
            background-color: var(--info);
            color: white;
        }
        
        .btn-mark-completed {
            background-color: var(--success);
            color: white;
        }
        
        .btn-mark-cancelled {
            background-color: var(--danger);
            color: white;
        }
        
        /* Toast Notification */
        .toast {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background-color: var(--secondary);
            color: white;
            padding: 15px 25px;
            border-radius: 8px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            z-index: 3000;
            transform: translateY(100px);
            opacity: 0;
            transition: var(--transition);
            max-width: 400px;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .toast.active {
            transform: translateY(0);
            opacity: 1;
        }
        
        .toast-icon {
            font-size: 20px;
        }
        
        .toast.success .toast-icon {
            color: var(--success);
        }
        
        .toast.warning .toast-icon {
            color: var(--warning);
        }
        
        .toast.error .toast-icon {
            color: var(--danger);
        }
        
        /* Responsiveness */
        @media (max-width: 1200px) {
            .orders-table {
                display: block;
                overflow-x: auto;
            }
        }
        
        @media (max-width: 992px) {
            .admin-nav {
                flex-direction: column;
                gap: 20px;
                align-items: flex-start;
            }
            
            .admin-controls {
                width: 100%;
                justify-content: space-between;
            }
            
            .filter-controls {
                flex-direction: column;
                align-items: stretch;
            }
            
            .filter-group {
                width: 100%;
            }
            
            .filter-select, .filter-input {
                min-width: 100%;
            }
        }
        
        @media (max-width: 768px) {
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .orders-table th, .orders-table td {
                padding: 10px 15px;
            }
            
            .action-buttons {
                flex-direction: column;
            }
            
            .customer-info {
                grid-template-columns: 1fr;
            }
            
            .modal-actions {
                flex-direction: column;
            }
            
            .btn-modal {
                width: 100%;
            }
        }
        
        @media (max-width: 576px) {
            .container {
                padding: 0 15px;
            }
            
            .stat-card {
                flex-direction: column;
                text-align: center;
            }
            
            .filter-header {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }
        }
        
        /* Real-time indicator */
        .real-time-indicator {
            position: fixed;
            top: 20px;
            right: 20px;
            background-color: var(--success);
            color: white;
            padding: 10px 20px;
            border-radius: 50px;
            font-size: 12px;
            font-weight: 600;
            z-index: 1001;
            display: flex;
            align-items: center;
            gap: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            animation: slideInRight 0.5s ease;
        }
        
        @keyframes slideInRight {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }
    </style>
</head>
<body>
    <!-- Header Admin -->
    <header class="admin-header">
        <div class="container">
            <nav class="admin-nav">
                <div class="admin-logo">
                    <div class="admin-logo-icon">
                        <i class="fas fa-user-shield"></i>
                    </div>
                    <div class="admin-logo-text">Admin <span>PANGS!T</span></div>
                </div>
                
                <div class="admin-controls">
                    <div class="admin-status">
                        <div class="status-indicator"></div>
                        <span>Sistem Real-time Aktif</span>
                    </div>
                    <button class="refresh-btn" id="refreshBtn">
                        <i class="fas fa-sync-alt"></i>
                    </button>
                </div>
            </nav>
        </div>
    </header>

    <!-- Real-time Notification -->
    <div class="real-time-indicator" id="realTimeIndicator" style="display: none;">
        <i class="fas fa-bell"></i>
        <span id="notificationText"></span>
    </div>

    <!-- Dashboard Stats -->
    <section class="dashboard-stats">
        <div class="container">
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-icon pending">
                        <i class="fas fa-clock"></i>
                    </div>
                    <div class="stat-info">
                        <h3>Menunggu</h3>
                        <div class="stat-number" id="pendingCount">0</div>
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-icon processing">
                        <i class="fas fa-spinner"></i>
                    </div>
                    <div class="stat-info">
                        <h3>Diproses</h3>
                        <div class="stat-number" id="processingCount">0</div>
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-icon completed">
                        <i class="fas fa-check-circle"></i>
                    </div>
                    <div class="stat-info">
                        <h3>Selesai</h3>
                        <div class="stat-number" id="completedCount">0</div>
                    </div>
                </div>
                
                <div class="stat-card">
                    <div class="stat-icon revenue">
                        <i class="fas fa-money-bill-wave"></i>
                    </div>
                    <div class="stat-info">
                        <h3>Pendapatan Hari Ini</h3>
                        <div class="stat-number" id="revenueToday">Rp 0</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Filter Controls -->
    <section class="filter-section">
        <div class="container">
            <div class="filter-header">
                <h2>Daftar Pesanan</h2>
                <div class="orders-count">
                    Total: <span id="totalOrdersCount">0</span> pesanan
                </div>
            </div>
            
            <div class="filter-controls">
                <div class="filter-group">
                    <label for="statusFilter">Status Pesanan</label>
                    <select id="statusFilter" class="filter-select">
                        <option value="all">Semua Status</option>
                        <option value="pending">Menunggu</option>
                        <option value="processing">Diproses</option>
                        <option value="completed">Selesai</option>
                        <option value="cancelled">Dibatalkan</option>
                    </select>
                </div>
                
                <div class="filter-group">
                    <label for="dateFilter">Tanggal Pesanan</label>
                    <input type="date" id="dateFilter" class="filter-input">
                </div>
                
                <div class="filter-group">
                    <label for="searchFilter">Cari (ID/Nama)</label>
                    <input type="text" id="searchFilter" class="filter-input" placeholder="ID atau nama pelanggan">
                </div>
                
                <div class="filter-actions">
                    <button class="btn-filter" id="applyFilter">Terapkan Filter</button>
                    <button class="btn-reset" id="resetFilter">Reset</button>
                </div>
            </div>
        </div>
    </section>

    <!-- Orders Table -->
    <section class="orders-section">
        <div class="container">
            <div class="orders-table-container">
                <table class="orders-table" id="ordersTable">
                    <thead>
                        <tr>
                            <th>Order ID</th>
                            <th>Tanggal/Waktu</th>
                            <th>Pelanggan</th>
                            <th>Items</th>
                            <th>Total</th>
                            <th>Status</th>
                            <th>Aksi</th>
                        </tr>
                    </thead>
                    <tbody id="ordersTableBody">
                        <!-- Data pesanan akan diisi oleh JavaScript -->
                    </tbody>
                </table>
                
                <div class="empty-orders" id="emptyOrdersMessage" style="display: none;">
                    <div class="empty-icon">
                        <i class="fas fa-shopping-cart"></i>
                    </div>
                    <h3>Tidak ada pesanan</h3>
                    <p>Tidak ada pesanan yang ditemukan dengan filter yang diterapkan</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Order Detail Modal -->
    <div class="order-modal" id="orderModal">
        <div class="order-modal-content">
            <button class="close-modal" id="closeOrderModal">&times;</button>
            
            <div class="modal-header">
                <h2>Detail Pesanan</h2>
                <div class="modal-order-id" id="modalOrderId"></div>
            </div>
            
            <div class="modal-body">
                <div class="modal-section">
                    <h3>Informasi Pelanggan</h3>
                    <div class="customer-info" id="customerInfo">
                        <!-- Informasi pelanggan akan diisi oleh JavaScript -->
                    </div>
                </div>
                
                <div class="modal-section">
                    <h3>Items Pesanan</h3>
                    <div class="order-items-list" id="modalOrderItems">
                        <!-- Items pesanan akan diisi oleh JavaScript -->
                    </div>
                </div>
                
                <div class="modal-section">
                    <h3>Ringkasan Pembayaran</h3>
                    <div class="order-summary" id="modalOrderSummary">
                        <!-- Ringkasan pesanan akan diisi oleh JavaScript -->
                    </div>
                </div>
                
                <div class="modal-section">
                    <h3>Status Pesanan</h3>
                    <div id="modalOrderStatus">
                        <!-- Status pesanan akan diisi oleh JavaScript -->
                    </div>
                </div>
                
                <div class="modal-actions" id="modalActions">
                    <!-- Tombol aksi akan diisi oleh JavaScript -->
                </div>
            </div>
        </div>
    </div>

    <!-- Toast Notification -->
    <div class="toast" id="toast">
        <div class="toast-icon">
            <i class="fas fa-info-circle"></i>
        </div>
        <div class="toast-message" id="toastMessage"></div>
    </div>

    <script>
        // Data pesanan dari localStorage
        let orders = [];
        let filteredOrders = [];
        
        // DOM Elements
        const refreshBtn = document.getElementById('refreshBtn');
        const pendingCount = document.getElementById('pendingCount');
        const processingCount = document.getElementById('processingCount');
        const completedCount = document.getElementById('completedCount');
        const revenueToday = document.getElementById('revenueToday');
        const totalOrdersCount = document.getElementById('totalOrdersCount');
        const ordersTableBody = document.getElementById('ordersTableBody');
        const emptyOrdersMessage = document.getElementById('emptyOrdersMessage');
        const orderModal = document.getElementById('orderModal');
        const closeOrderModal = document.getElementById('closeOrderModal');
        const realTimeIndicator = document.getElementById('realTimeIndicator');
        const notificationText = document.getElementById('notificationText');
        const toast = document.getElementById('toast');
        const toastMessage = document.getElementById('toastMessage');
        
        // Filter elements
        const statusFilter = document.getElementById('statusFilter');
        const dateFilter = document.getElementById('dateFilter');
        const searchFilter = document.getElementById('searchFilter');
        const applyFilter = document.getElementById('applyFilter');
        const resetFilter = document.getElementById('resetFilter');
        
        // Format Rupiah
        function formatRupiah(amount) {
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(amount);
        }
        
        // Format tanggal
        function formatDate(timestamp) {
            const date = new Date(timestamp);
            return date.toLocaleDateString('id-ID', {
                day: '2-digit',
                month: '2-digit',
                year: 'numeric'
            });
        }
        
        // Format waktu
        function formatTime(timestamp) {
            const date = new Date(timestamp);
            return date.toLocaleTimeString('id-ID', {
                hour: '2-digit',
                minute: '2-digit'
            });
        }
        
        // Load orders from localStorage
        function loadOrders() {
            const storedOrders = localStorage.getItem('pangsit_admin_orders');
            orders = storedOrders ? JSON.parse(storedOrders) : [];
            
            // Sort by latest first
            orders.sort((a, b) => b.timestamp - a.timestamp);
            
            // Set default filtered orders
            filteredOrders = [...orders];
            
            updateDashboardStats();
            renderOrdersTable();
        }
        
        // Update dashboard statistics
        function updateDashboardStats() {
            const today = new Date().toLocaleDateString('id-ID');
            
            // Filter orders by status
            const pendingOrders = orders.filter(order => order.status === 'pending');
            const processingOrders = orders.filter(order => order.status === 'processing');
            const completedOrders = orders.filter(order => order.status === 'completed');
            
            // Calculate today's revenue
            const todayRevenue = orders
                .filter(order => order.date === today && order.status === 'completed')
                .reduce((sum, order) => sum + order.total, 0);
            
            // Update counts
            pendingCount.textContent = pendingOrders.length;
            processingCount.textContent = processingOrders.length;
            completedCount.textContent = completedOrders.length;
            revenueToday.textContent = formatRupiah(todayRevenue);
        }
        
        // Render orders table
        function renderOrdersTable() {
            ordersTableBody.innerHTML = '';
            
            if (filteredOrders.length === 0) {
                emptyOrdersMessage.style.display = 'block';
                totalOrdersCount.textContent = '0';
                return;
            }
            
            emptyOrdersMessage.style.display = 'none';
            totalOrdersCount.textContent = filteredOrders.length.toString();
            
            filteredOrders.forEach(order => {
                const row = document.createElement('tr');
                
                // Status badge
                let statusBadge = '';
                switch(order.status) {
                    case 'pending':
                        statusBadge = '<span class="status-badge status-pending">Menunggu</span>';
                        break;
                    case 'processing':
                        statusBadge = '<span class="status-badge status-processing">Diproses</span>';
                        break;
                    case 'completed':
                        statusBadge = '<span class="status-badge status-completed">Selesai</span>';
                        break;
                    case 'cancelled':
                        statusBadge = '<span class="status-badge status-cancelled">Dibatalkan</span>';
                        break;
                }
                
                // Customer info
                const customerInfo = `
                    <div class="customer-name">${order.customer.name}</div>
                    <div class="customer-phone">${order.customer.phone}</div>
                `;
                
                // Order items (limit to 2 items for table display)
                const itemsDisplay = order.products.slice(0, 2).map(item => `
                    <div class="order-item">
                        <div class="item-name">${item.name}</div>
                        <div>${item.quantity}x</div>
                    </div>
                `).join('');
                
                const moreItems = order.products.length > 2 
                    ? `<div class="order-item" style="font-style: italic; color: var(--gray);">
                         +${order.products.length - 2} item lainnya
                       </div>` 
                    : '';
                
                row.innerHTML = `
                    <td>
                        <div class="order-id">${order.id}</div>
                    </td>
                    <td>
                        <div>${order.date}</div>
                        <div style="font-size: 13px; color: var(--gray);">${order.time}</div>
                    </td>
                    <td>
                        <div class="order-customer">
                            ${customerInfo}
                        </div>
                    </td>
                    <td>
                        <div class="order-items">
                            ${itemsDisplay}
                            ${moreItems}
                        </div>
                    </td>
                    <td>
                        <div class="order-total">${formatRupiah(order.total)}</div>
                    </td>
                    <td>${statusBadge}</td>
                    <td>
                        <div class="action-buttons">
                            <button class="btn-action btn-view" data-id="${order.id}" title="Lihat Detail">
                                <i class="fas fa-eye"></i>
                            </button>
                            ${order.status === 'pending' ? `
                                <button class="btn-action btn-process" data-id="${order.id}" title="Proses Pesanan">
                                    <i class="fas fa-play"></i>
                                </button>
                                <button class="btn-action btn-cancel" data-id="${order.id}" title="Batalkan Pesanan">
                                    <i class="fas fa-times"></i>
                                </button>
                            ` : ''}
                            ${order.status === 'processing' ? `
                                <button class="btn-action btn-process" data-id="${order.id}" title="Tandai Selesai">
                                    <i class="fas fa-check"></i>
                                </button>
                            ` : ''}
                        </div>
                    </td>
                `;
                
                ordersTableBody.appendChild(row);
            });
            
            // Add event listeners to action buttons
            document.querySelectorAll('.btn-view').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    showOrderDetail(orderId);
                });
            });
            
            document.querySelectorAll('.btn-process').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    const order = orders.find(o => o.id === orderId);
                    
                    if (order.status === 'pending') {
                        updateOrderStatus(orderId, 'processing');
                    } else if (order.status === 'processing') {
                        updateOrderStatus(orderId, 'completed');
                    }
                });
            });
            
            document.querySelectorAll('.btn-cancel').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    if (confirm('Apakah Anda yakin ingin membatalkan pesanan ini?')) {
                        updateOrderStatus(orderId, 'cancelled');
                    }
                });
            });
        }
        
        // Show order detail in modal
        function showOrderDetail(orderId) {
            const order = orders.find(o => o.id === orderId);
            if (!order) return;
            
            // Set modal title
            document.getElementById('modalOrderId').textContent = order.id;
            
            // Customer info
            const customerInfo = document.getElementById('customerInfo');
            customerInfo.innerHTML = `
                <div class="info-item">
                    <div class="info-label">Nama Lengkap</div>
                    <div>${order.customer.name}</div>
                </div>
                <div class="info-item">
                    <div class="info-label">Nomor Telepon</div>
                    <div>${order.customer.phone}</div>
                </div>
                <div class="info-item">
                    <div class="info-label">Alamat Pengiriman</div>
                    <div>${order.customer.address}</div>
                </div>
                <div class="info-item">
                    <div class="info-label">Metode Pembayaran</div>
                    <div>${order.paymentMethod.toUpperCase()}</div>
                </div>
                ${order.notes ? `
                <div class="info-item">
                    <div class="info-label">Catatan Pesanan</div>
                    <div>${order.notes}</div>
                </div>
                ` : ''}
            `;
            
            // Order items
            const modalOrderItems = document.getElementById('modalOrderItems');
            modalOrderItems.innerHTML = '';
            
            order.products.forEach(item => {
                const itemElement = document.createElement('div');
                itemElement.className = 'order-item-detail';
                itemElement.innerHTML = `
                    <img src="${item.image || 'foto/default.jpg'}" alt="${item.name}" class="item-image" onerror="this.src='foto/default.jpg'">
                    <div class="item-info">
                        <div class="item-name">${item.name}</div>
                        <div>${item.quantity} x ${formatRupiah(item.price)}</div>
                    </div>
                    <div class="item-price">
                        ${formatRupiah(item.price * item.quantity)}
                    </div>
                `;
                modalOrderItems.appendChild(itemElement);
            });
            
            // Order summary
            const modalOrderSummary = document.getElementById('modalOrderSummary');
            modalOrderSummary.innerHTML = `
                <div class="summary-row">
                    <span>Subtotal</span>
                    <span>${formatRupiah(order.subtotal)}</span>
                </div>
                <div class="summary-row">
                    <span>Pengiriman</span>
                    <span>${formatRupiah(order.shipping)}</span>
                </div>
                <div class="summary-row">
                    <span>Pajak (10%)</span>
                    <span>${formatRupiah(order.tax)}</span>
                </div>
                <div class="summary-row total">
                    <span>Total</span>
                    <span>${formatRupiah(order.total)}</span>
                </div>
            `;
            
            // Order status
            const modalOrderStatus = document.getElementById('modalOrderStatus');
            let statusText = '';
            let statusClass = '';
            
            switch(order.status) {
                case 'pending':
                    statusText = 'Menunggu Konfirmasi';
                    statusClass = 'status-pending';
                    break;
                case 'processing':
                    statusText = 'Sedang Diproses';
                    statusClass = 'status-processing';
                    break;
                case 'completed':
                    statusText = 'Pesanan Selesai';
                    statusClass = 'status-completed';
                    break;
                case 'cancelled':
                    statusText = 'Pesanan Dibatalkan';
                    statusClass = 'status-cancelled';
                    break;
            }
            
            modalOrderStatus.innerHTML = `
                <span class="status-badge ${statusClass}" style="font-size: 14px; padding: 8px 15px;">
                    ${statusText}
                </span>
                <div style="margin-top: 10px; color: var(--gray); font-size: 14px;">
                    Pesanan dibuat: ${order.date} ${order.time}
                </div>
            `;
            
            // Modal actions
            const modalActions = document.getElementById('modalActions');
            modalActions.innerHTML = '';
            
            if (order.status === 'pending') {
                modalActions.innerHTML = `
                    <button class="btn-modal btn-mark-processing" id="markAsProcessing">Tandai sebagai Diproses</button>
                    <button class="btn-modal btn-mark-cancelled" id="markAsCancelled">Batalkan Pesanan</button>
                `;
            } else if (order.status === 'processing') {
                modalActions.innerHTML = `
                    <button class="btn-modal btn-mark-completed" id="markAsCompleted">Tandai sebagai Selesai</button>
                `;
            } else if (order.status === 'completed') {
                modalActions.innerHTML = `
                    <div style="color: var(--success); font-weight: 600;">
                        <i class="fas fa-check-circle"></i> Pesanan ini sudah selesai
                    </div>
                `;
            } else if (order.status === 'cancelled') {
                modalActions.innerHTML = `
                    <div style="color: var(--danger); font-weight: 600;">
                        <i class="fas fa-times-circle"></i> Pesanan ini sudah dibatalkan
                    </div>
                `;
            }
            
            // Add event listeners to modal action buttons
            if (document.getElementById('markAsProcessing')) {
                document.getElementById('markAsProcessing').addEventListener('click', () => {
                    updateOrderStatus(order.id, 'processing');
                    orderModal.classList.remove('active');
                });
            }
            
            if (document.getElementById('markAsCompleted')) {
                document.getElementById('markAsCompleted').addEventListener('click', () => {
                    updateOrderStatus(order.id, 'completed');
                    orderModal.classList.remove('active');
                });
            }
            
            if (document.getElementById('markAsCancelled')) {
                document.getElementById('markAsCancelled').addEventListener('click', () => {
                    if (confirm('Apakah Anda yakin ingin membatalkan pesanan ini?')) {
                        updateOrderStatus(order.id, 'cancelled');
                        orderModal.classList.remove('active');
                    }
                });
            }
            
            // Show modal
            orderModal.classList.add('active');
        }
        
        // Update order status
        function updateOrderStatus(orderId, newStatus) {
            // Find order index
            const orderIndex = orders.findIndex(o => o.id === orderId);
            if (orderIndex === -1) return;
            
            // Update order
            orders[orderIndex].status = newStatus;
            
            // Save to localStorage
            localStorage.setItem('pangsit_admin_orders', JSON.stringify(orders));
            
            // Update filtered orders
            const filteredOrderIndex = filteredOrders.findIndex(o => o.id === orderId);
            if (filteredOrderIndex !== -1) {
                filteredOrders[filteredOrderIndex].status = newStatus;
            }
            
            // Update UI
            updateDashboardStats();
            renderOrdersTable();
            
            // Show toast notification
            showToast(`Status pesanan ${orderId} diubah menjadi "${getStatusText(newStatus)}"`, 'success');
            
            // If from modal, close modal
            if (orderModal.classList.contains('active')) {
                orderModal.classList.remove('active');
            }
        }
        
        // Get status text
        function getStatusText(status) {
            switch(status) {
                case 'pending': return 'Menunggu';
                case 'processing': return 'Diproses';
                case 'completed': return 'Selesai';
                case 'cancelled': return 'Dibatalkan';
                default: return status;
            }
        }
        
        // Apply filters
        function applyOrderFilters() {
            const status = statusFilter.value;
            const date = dateFilter.value;
            const search = searchFilter.value.toLowerCase();
            
            filteredOrders = orders.filter(order => {
                // Filter by status
                if (status !== 'all' && order.status !== status) return false;
                
                // Filter by date
                if (date) {
                    const orderDate = new Date(order.timestamp).toISOString().split('T')[0];
                    if (orderDate !== date) return false;
                }
                
                // Filter by search
                if (search) {
                    const matchesId = order.id.toLowerCase().includes(search);
                    const matchesName = order.customer.name.toLowerCase().includes(search);
                    const matchesPhone = order.customer.phone.includes(search);
                    
                    if (!matchesId && !matchesName && !matchesPhone) return false;
                }
                
                return true;
            });
            
            renderOrdersTable();
        }
        
        // Reset filters
        function resetOrderFilters() {
            statusFilter.value = 'all';
            dateFilter.value = '';
            searchFilter.value = '';
            filteredOrders = [...orders];
            renderOrdersTable();
        }
        
        // Show toast notification
        function showToast(message, type = 'info') {
            // Set message and type
            toastMessage.textContent = message;
            toast.className = `toast ${type}`;
            
            // Change icon based on type
            const toastIcon = toast.querySelector('.toast-icon i');
            switch(type) {
                case 'success':
                    toastIcon.className = 'fas fa-check-circle';
                    break;
                case 'warning':
                    toastIcon.className = 'fas fa-exclamation-triangle';
                    break;
                case 'error':
                    toastIcon.className = 'fas fa-times-circle';
                    break;
                default:
                    toastIcon.className = 'fas fa-info-circle';
            }
            
            // Show toast
            toast.classList.add('active');
            
            // Auto hide after 5 seconds
            setTimeout(() => {
                toast.classList.remove('active');
            }, 5000);
        }
        
        // Show real-time notification
        function showRealTimeNotification(order) {
            notificationText.textContent = `Pesanan baru: ${order.id} dari ${order.customer.name}`;
            realTimeIndicator.style.display = 'flex';
            
            // Auto hide after 5 seconds
            setTimeout(() => {
                realTimeIndicator.style.display = 'none';
            }, 5000);
            
            // Play notification sound (if browser allows)
            try {
                const audio = new Audio('https://assets.mixkit.co/sfx/preview/mixkit-bell-notification-933.mp3');
                audio.volume = 0.3;
                audio.play().catch(e => console.log('Audio play failed:', e));
            } catch (e) {
                console.log('Notification sound not available');
            }
        }
        
        // Check for new orders
        function checkForNewOrders() {
            const lastCheckTime = localStorage.getItem('pangsit_last_check_time') || 0;
            const newOrdersFlag = localStorage.getItem('pangsit_new_order');
            
            if (newOrdersFlag) {
                try {
                    const newOrder = JSON.parse(newOrdersFlag);
                    
                    // Check if this order is newer than our last check
                    if (newOrder.timestamp > lastCheckTime) {
                        // Update last check time
                        localStorage.setItem('pangsit_last_check_time', Date.now().toString());
                        
                        // Clear the flag
                        localStorage.removeItem('pangsit_new_order');
                        
                        // Reload orders to get the new one
                        loadOrders();
                        
                        // Show notification
                        showRealTimeNotification(newOrder);
                        showToast(`Pesanan baru diterima: ${newOrder.id}`, 'success');
                    }
                } catch (e) {
                    console.error('Error parsing new order:', e);
                }
            }
            
            // Check every 3 seconds for real-time updates
            setTimeout(checkForNewOrders, 3000);
        }
        
        // Initialize
        function init() {
            // Load orders
            loadOrders();
            
            // Set up event listeners
            refreshBtn.addEventListener('click', () => {
                loadOrders();
                showToast('Data pesanan diperbarui', 'success');
            });
            
            applyFilter.addEventListener('click', applyOrderFilters);
            resetFilter.addEventListener('click', resetOrderFilters);
            
            // Close modal
            closeOrderModal.addEventListener('click', () => {
                orderModal.classList.remove('active');
            });
            
            orderModal.addEventListener('click', (e) => {
                if (e.target === orderModal) {
                    orderModal.classList.remove('active');
                }
            });
            
            // Initialize real-time checking
            checkForNewOrders();
            
            // Set today's date as default in date filter
            const today = new Date().toISOString().split('T')[0];
            dateFilter.value = today;
            
            // Apply today's filter by default
            applyOrderFilters();
            
            console.log('✅ Admin PANGS!T berhasil diinisialisasi');
            console.log('📊 Total pesanan:', orders.length);
            console.log('🔄 Sistem real-time aktif');
            
            // Add some sample data if no orders exist
            if (orders.length === 0) {
                console.log('ℹ️ Tidak ada data pesanan. Menambahkan data contoh...');
                addSampleOrders();
            }
        }
        
        // Add sample orders for testing
        function addSampleOrders() {
            const sampleOrders = [
                {
                    id: 'ORD-20241225-143025-001',
                    customer: {
                        name: 'Budi Santoso',
                        phone: '+62 812-3456-7890',
                        address: 'Jl. Merdeka No. 123, Jakarta'
                    },
                    products: [
                        {
                            name: 'fire silk wonton',
                            price: 20000,
                            quantity: 2,
                            image: 'foto/fire silk wonton.jpg'
                        },
                        {
                            name: 'crispy melt deluxe',
                            price: 13000,
                            quantity: 1,
                            image: 'foto/crispy melt deluxe.jpg'
                        }
                    ],
                    paymentMethod: 'gopay',
                    status: 'completed',
                    date: '25/12/2024',
                    time: '14:30',
                    timestamp: new Date(2024, 11, 25, 14, 30, 25).getTime(),
                    notes: 'Tolong tambah saus pedas',
                    shipping: 15000,
                    tax: 5300,
                    subtotal: 53000,
                    total: 73300
                },
                {
                    id: 'ORD-20241225-152045-002',
                    customer: {
                        name: 'Siti Aisyah',
                        phone: '+62 813-9876-5432',
                        address: 'Jl. Panjaitan No. 45, Tangerang'
                    },
                    products: [
                        {
                            name: 'Golden chili crunch',
                            price: 15000,
                            quantity: 3,
                            image: 'foto/Golden chili crunch.jpg'
                        }
                    ],
                    paymentMethod: 'gopay',
                    status: 'processing',
                    date: '25/12/2024',
                    time: '15:20',
                    timestamp: new Date(2024, 11, 25, 15, 20, 45).getTime(),
                    notes: '',
                    shipping: 15000,
                    tax: 4500,
                    subtotal: 45000,
                    total: 64500
                },
                {
                    id: 'ORD-20241225-161510-003',
                    customer: {
                        name: 'Ahmad Rizki',
                        phone: '+62 821-1122-3344',
                        address: 'Jl. Sudirman No. 78, Bekasi'
                    },
                    products: [
                        {
                            name: 'pangsit kuah mercon',
                            price: 20000,
                            quantity: 1,
                            image: 'foto/pangsit kuah mercon.jpg'
                        },
                        {
                            name: 'pangsit isi tahu',
                            price: 15000,
                            quantity: 2,
                            image: 'foto/pangsit isi tahu.jpg'
                        }
                    ],
                    paymentMethod: 'gopay',
                    status: 'pending',
                    date: '25/12/2024',
                    time: '16:15',
                    timestamp: new Date(2024, 11, 25, 16, 15, 10).getTime(),
                    notes: 'Tanpa MSG ya',
                    shipping: 15000,
                    tax: 5500,
                    subtotal: 50000,
                    total: 70500
                }
            ];
            
            // Save to localStorage
            localStorage.setItem('pangsit_admin_orders', JSON.stringify(sampleOrders));
            
            // Reload orders
            loadOrders();
            
            showToast('Data contoh pesanan ditambahkan', 'info');
        }
        
        // Export data function
        function exportOrdersData() {
            const dataStr = JSON.stringify(orders, null, 2);
            const dataBlob = new Blob([dataStr], { type: 'application/json' });
            const url = URL.createObjectURL(dataBlob);
            
            const link = document.createElement('a');
            link.href = url;
            link.download = `pangsit_orders_${new Date().toISOString().split('T')[0]}.json`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            
            showToast('Data pesanan berhasil diekspor', 'success');
        }
        
        // Add export button dynamically
        function addExportButton() {
            const headerControls = document.querySelector('.admin-controls');
            const exportBtn = document.createElement('button');
            exportBtn.innerHTML = '<i class="fas fa-download"></i>';
            exportBtn.className = 'refresh-btn';
            exportBtn.title = 'Ekspor Data';
            exportBtn.style.marginRight = '10px';
            exportBtn.addEventListener('click', exportOrdersData);
            
            headerControls.insertBefore(exportBtn, refreshBtn);
        }
        
        // Add keyboard shortcuts
        function addKeyboardShortcuts() {
            document.addEventListener('keydown', (e) => {
                // Ctrl+R to refresh
                if (e.ctrlKey && e.key === 'r') {
                    e.preventDefault();
                    refreshBtn.click();
                }
                
                // Escape to close modal
                if (e.key === 'Escape' && orderModal.classList.contains('active')) {
                    orderModal.classList.remove('active');
                }
                
                // Ctrl+E to export
                if (e.ctrlKey && e.key === 'e') {
                    e.preventDefault();
                    exportOrdersData();
                }
            });
        }
        
        // Initialize when DOM is loaded
        document.addEventListener('DOMContentLoaded', () => {
            init();
            addExportButton();
            addKeyboardShortcuts();
            
            // Add instructions
            console.log(`
            ============================================
            ADMIN PANGS!T - INSTRUKSI PENGGUNAAN
            ============================================
            1. Sistem otomatis memantau pesanan baru
            2. Filter pesanan berdasarkan status/tanggal
            3. Klik mata 👁️ untuk melihat detail pesanan
            4. Klik tombol aksi untuk ubah status
            5. Ctrl+R = Refresh data
            6. Ctrl+E = Ekspor data
            7. Escape = Tutup modal
            ============================================
            `);
        });
        
        // Listen for new orders from other tabs
        window.addEventListener('storage', (e) => {
            if (e.key === 'pangsit_new_order') {
                console.log('📢 Pesanan baru terdeteksi dari tab lain');
                loadOrders();
                
                try {
                    const newOrder = JSON.parse(e.newValue);
                    if (newOrder) {
                        showRealTimeNotification(newOrder);
                    }
                } catch (error) {
                    console.log('Error parsing new order from storage:', error);
                }
            }
        });
        
        // Custom event listener for same-tab communication
        window.addEventListener('newPangsitOrder', (e) => {
            console.log('📢 Pesanan baru dari event custom:', e.detail.id);
            loadOrders();
            showRealTimeNotification(e.detail);
        });
    </script>
</body>
</html>
