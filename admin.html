<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin PANGS!T - Dashboard</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* RESET & VARIABLES */
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
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', sans-serif;
        }
        
        body {
            background: #f5f7fa;
            color: var(--dark);
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* HEADER */
        .admin-header {
            background: linear-gradient(135deg, var(--secondary) 0%, #1a1c2f 100%);
            color: white;
            padding: 15px 0;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .logo h1 {
            font-size: 24px;
            color: var(--primary);
        }
        
        .logo span {
            color: white;
        }
        
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .avatar {
            width: 40px;
            height: 40px;
            background: var(--primary);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 18px;
        }
        
        .logout-btn {
            background: rgba(255,255,255,0.1);
            border: 1px solid rgba(255,255,255,0.2);
            color: white;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        /* MAIN CONTENT */
        .admin-main {
            padding: 25px 0;
        }
        
        .page-title {
            margin-bottom: 25px;
        }
        
        .page-title h2 {
            font-size: 28px;
            color: var(--secondary);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .live-badge {
            background: var(--danger);
            color: white;
            font-size: 12px;
            padding: 4px 10px;
            border-radius: 15px;
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.7; }
            100% { opacity: 1; }
        }
        
        /* STATS CARDS */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 25px;
        }
        
        .stat-card {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.08);
            display: flex;
            align-items: center;
            gap: 15px;
            cursor: pointer;
            transition: 0.3s;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 15px rgba(0,0,0,0.1);
        }
        
        .stat-icon {
            width: 50px;
            height: 50px;
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            color: white;
        }
        
        .icon-pending { background: var(--warning); }
        .icon-processing { background: var(--info); }
        .icon-completed { background: var(--success); }
        .icon-total { background: var(--primary); }
        
        .stat-info h3 {
            font-size: 24px;
            margin-bottom: 5px;
        }
        
        .stat-info p {
            color: var(--gray);
            font-size: 14px;
        }
        
        /* CONTROLS */
        .controls {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.08);
            margin-bottom: 25px;
            display: flex;
            gap: 15px;
            flex-wrap: wrap;
        }
        
        .search-box {
            flex: 1;
            min-width: 250px;
            position: relative;
        }
        
        .search-box input {
            width: 100%;
            padding: 10px 15px 10px 40px;
            border: 1px solid var(--light-gray);
            border-radius: 6px;
            font-size: 16px;
        }
        
        .search-icon {
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
        }
        
        .filter-buttons {
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }
        
        .filter-btn {
            padding: 8px 15px;
            background: white;
            border: 1px solid var(--light-gray);
            border-radius: 6px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .filter-btn.active {
            background: var(--primary);
            color: white;
            border-color: var(--primary);
        }
        
        /* ORDERS TABLE */
        .table-container {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 4px 8px rgba(0,0,0,0.08);
            margin-bottom: 30px;
        }
        
        .table-header {
            padding: 15px 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .refresh-btn {
            background: white;
            border: 1px solid var(--light-gray);
            padding: 6px 12px;
            border-radius: 5px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
        }
        
        .refresh-btn.rotating {
            animation: rotate 1s linear infinite;
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        thead {
            background: var(--light-gray);
        }
        
        th {
            padding: 15px;
            text-align: left;
            font-weight: 600;
            color: var(--secondary);
        }
        
        td {
            padding: 15px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        tr:hover {
            background: rgba(255,107,53,0.05);
        }
        
        .order-id {
            font-weight: bold;
            color: var(--secondary);
            font-family: monospace;
        }
        
        .customer-name {
            font-weight: 600;
        }
        
        .customer-phone {
            color: var(--gray);
            font-size: 14px;
        }
        
        .status-badge {
            display: inline-block;
            padding: 4px 10px;
            border-radius: 15px;
            font-size: 12px;
            font-weight: 600;
        }
        
        .status-pending { background: #fff3cd; color: #856404; }
        .status-processing { background: #d1ecf1; color: #0c5460; }
        .status-completed { background: #d4edda; color: #155724; }
        .status-cancelled { background: #f8d7da; color: #721c24; }
        
        .action-buttons {
            display: flex;
            gap: 5px;
        }
        
        .action-btn {
            width: 32px;
            height: 32px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
        }
        
        .btn-view { background: var(--info); }
        .btn-edit { background: var(--primary); }
        .btn-whatsapp { background: #25D366; }
        
        /* NO ORDERS */
        .no-orders {
            text-align: center;
            padding: 50px 20px;
            color: var(--gray);
        }
        
        /* MODAL */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.8);
            z-index: 2000;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        
        .modal.active {
            display: flex;
        }
        
        .modal-content {
            background: white;
            border-radius: 10px;
            max-width: 800px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            animation: slideIn 0.3s ease;
        }
        
        @keyframes slideIn {
            from {
                transform: translateY(-50px);
                opacity: 0;
            }
            to {
                transform: translateY(0);
                opacity: 1;
            }
        }
        
        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            background: none;
            border: none;
            font-size: 24px;
            color: var(--gray);
            cursor: pointer;
        }
        
        .modal-header {
            padding: 20px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .modal-header h3 {
            color: var(--secondary);
            font-size: 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .modal-body {
            padding: 20px;
        }
        
        .order-details-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        
        .detail-section {
            margin-bottom: 20px;
        }
        
        .detail-section h4 {
            color: var(--secondary);
            margin-bottom: 10px;
            padding-bottom: 8px;
            border-bottom: 2px solid var(--light-gray);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .detail-item {
            display: flex;
            margin-bottom: 8px;
            font-size: 14px;
        }
        
        .detail-label {
            font-weight: 600;
            width: 120px;
            color: var(--secondary);
            flex-shrink: 0;
        }
        
        .modal-footer {
            padding: 15px 20px;
            border-top: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .status-select {
            padding: 8px 12px;
            border-radius: 5px;
            border: 1px solid var(--light-gray);
            min-width: 150px;
        }
        
        /* NOTIFICATION */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: var(--success);
            color: white;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
            z-index: 3000;
            animation: slideInRight 0.3s ease;
            max-width: 350px;
        }
        
        .notification.error { background: var(--danger); }
        .notification.warning { background: var(--warning); }
        
        @keyframes slideInRight {
            from {
                transform: translateX(100%);
                opacity: 0;
            }
            to {
                transform: translateX(0);
                opacity: 1;
            }
        }
        
        /* RESPONSIVE */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 10px;
                text-align: center;
            }
            
            .controls {
                flex-direction: column;
            }
            
            .table-container {
                overflow-x: auto;
            }
            
            table {
                min-width: 800px;
            }
            
            .modal-body {
                padding: 15px;
            }
            
            .order-details-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- HEADER -->
    <header class="admin-header">
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <i class="fas fa-dumpling"></i>
                    <h1>PANGS!T <span>Admin</span></h1>
                </div>
                <div class="user-info">
                    <div class="avatar">A</div>
                    <div>
                        <div style="font-weight: 600;">Administrator</div>
                        <div style="font-size: 14px; opacity: 0.8;">Dashboard Manager</div>
                    </div>
                    <button class="logout-btn" id="logoutBtn">
                        <i class="fas fa-sign-out-alt"></i> Logout
                    </button>
                </div>
            </div>
        </div>
    </header>
    
    <!-- MAIN CONTENT -->
    <main class="admin-main">
        <div class="container">
            <!-- PAGE TITLE -->
            <div class="page-title">
                <h2>
                    <i class="fas fa-shopping-cart"></i>
                    Dashboard Pesanan
                    <span class="live-badge">
                        <i class="fas fa-circle" style="font-size: 8px;"></i> LIVE
                    </span>
                </h2>
                <p>Auto-refresh setiap 30 detik - Pesanan baru muncul otomatis</p>
            </div>
            
            <!-- STATS -->
            <div class="stats-grid">
                <div class="stat-card" data-filter="pending">
                    <div class="stat-icon icon-pending">
                        <i class="fas fa-clock"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="pendingCount">0</h3>
                        <p>Menunggu</p>
                    </div>
                </div>
                
                <div class="stat-card" data-filter="processing">
                    <div class="stat-icon icon-processing">
                        <i class="fas fa-truck"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="processingCount">0</h3>
                        <p>Diproses</p>
                    </div>
                </div>
                
                <div class="stat-card" data-filter="completed">
                    <div class="stat-icon icon-completed">
                        <i class="fas fa-check-circle"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="completedCount">0</h3>
                        <p>Selesai</p>
                    </div>
                </div>
                
                <div class="stat-card" data-filter="all">
                    <div class="stat-icon icon-total">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <div class="stat-info">
                        <h3 id="totalCount">0</h3>
                        <p>Total Pesanan</p>
                    </div>
                </div>
            </div>
            
            <!-- CONTROLS -->
            <div class="controls">
                <div class="search-box">
                    <i class="fas fa-search search-icon"></i>
                    <input type="text" id="searchInput" placeholder="Cari nama, telepon, atau ID...">
                </div>
                
                <div class="filter-buttons">
                    <button class="filter-btn active" data-filter="all">
                        <i class="fas fa-list"></i> Semua
                    </button>
                    <button class="filter-btn" data-filter="pending">
                        <i class="fas fa-clock"></i> Menunggu
                    </button>
                    <button class="filter-btn" data-filter="processing">
                        <i class="fas fa-truck"></i> Diproses
                    </button>
                    <button class="filter-btn" data-filter="completed">
                        <i class="fas fa-check-circle"></i> Selesai
                    </button>
                    <button class="filter-btn" data-filter="cancelled">
                        <i class="fas fa-times-circle"></i> Dibatalkan
                    </button>
                </div>
            </div>
            
            <!-- ORDERS TABLE -->
            <div class="table-container">
                <div class="table-header">
                    <h3><i class="fas fa-table"></i> Daftar Pesanan</h3>
                    <button class="refresh-btn" id="refreshBtn">
                        <i class="fas fa-sync-alt"></i> Refresh
                    </button>
                </div>
                
                <div style="overflow-x: auto;">
                    <table>
                        <thead>
                            <tr>
                                <th>ID Pesanan</th>
                                <th>Pelanggan</th>
                                <th>Produk</th>
                                <th>Total</th>
                                <th>Metode</th>
                                <th>Status</th>
                                <th>Tanggal</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="ordersTable">
                            <!-- Data akan dimuat di sini -->
                        </tbody>
                    </table>
                </div>
                
                <div id="noOrders" class="no-orders">
                    <i class="fas fa-shopping-cart fa-3x" style="margin-bottom: 15px;"></i>
                    <h3>Belum ada pesanan</h3>
                    <p>Pesanan dari pelanggan akan muncul di sini</p>
                </div>
            </div>
        </div>
    </main>
    
    <!-- ORDER DETAIL MODAL -->
    <div class="modal" id="orderDetailModal">
        <div class="modal-content">
            <button class="close-modal" id="closeModal">&times;</button>
            <div class="modal-header">
                <h3><i class="fas fa-file-invoice"></i> Detail Pesanan</h3>
            </div>
            <div class="modal-body" id="orderDetailContent">
                <!-- Konten akan diisi JavaScript -->
            </div>
            <div class="modal-footer">
                <select class="status-select" id="statusSelect">
                    <option value="pending">Menunggu Pembayaran</option>
                    <option value="processing">Sedang Diproses</option>
                    <option value="completed">Selesai</option>
                    <option value="cancelled">Dibatalkan</option>
                </select>
                <div style="display: flex; gap: 10px;">
                    <button class="btn-close" id="closeDetailBtn" style="background: var(--gray);">
                        <i class="fas fa-times"></i> Tutup
                    </button>
                    <button class="action-btn btn-edit" id="updateStatusBtn">
                        <i class="fas fa-save"></i> Update
                    </button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- LOGIN MODAL -->
    <div class="modal" id="loginModal" style="display: flex;">
        <div class="modal-content" style="max-width: 400px;">
            <div class="modal-header">
                <h3><i class="fas fa-lock"></i> Admin Login</h3>
            </div>
            <div class="modal-body">
                <div style="text-align: center; margin-bottom: 20px;">
                    <div style="font-size: 48px; color: var(--primary); margin-bottom: 10px;">
                        <i class="fas fa-dumpling"></i>
                    </div>
                    <h3 style="color: var(--secondary);">PANGS!T Admin</h3>
                    <p style="color: var(--gray);">Masuk untuk mengelola pesanan</p>
                </div>
                
                <form id="loginForm">
                    <div style="margin-bottom: 15px;">
                        <label style="display: block; margin-bottom: 5px; color: var(--secondary);">Username</label>
                        <input type="text" id="username" class="search-box" style="width: 100%;" placeholder="admin" value="admin">
                    </div>
                    
                    <div style="margin-bottom: 20px;">
                        <label style="display: block; margin-bottom: 5px; color: var(--secondary);">Password</label>
                        <input type="password" id="password" class="search-box" style="width: 100%;" placeholder="admin123" value="admin123">
                    </div>
                    
                    <button type="submit" class="refresh-btn" style="width: 100%; background: var(--primary); color: white; border: none; padding: 12px;">
                        <i class="fas fa-sign-in-alt"></i> Masuk
                    </button>
                    
                    <div id="loginError" style="color: var(--danger); text-align: center; margin-top: 10px; display: none;">
                        <i class="fas fa-exclamation-circle"></i> Username atau password salah
                    </div>
                </form>
            </div>
        </div>
    </div>

    <script>
        // ==================== KONFIGURASI ====================
        const ADMIN_CREDENTIALS = {
            username: "admin",
            password: "admin123"
        };
        
        const STORAGE_KEYS = {
            ADMIN_ORDERS: 'pangsit_admin_orders',
            NEW_ORDER_FLAG: 'pangsit_new_order',
            LOGGED_IN: 'pangsit_admin_logged_in'
        };
        
        // ==================== VARIABEL GLOBAL ====================
        let allOrders = [];
        let filteredOrders = [];
        let currentFilter = 'all';
        let currentSearch = '';
        let currentOrderId = null;
        let autoRefreshInterval = null;
        
        // ==================== FUNGSI UTAMA ====================
        
        // Format Rupiah
        function formatRupiah(amount) {
            if (!amount) return 'Rp 0';
            return 'Rp ' + amount.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ".");
        }
        
        // Format Tanggal
        function formatDate(timestamp) {
            if (!timestamp) return '-';
            const date = new Date(timestamp);
            return date.toLocaleDateString('id-ID', {
                day: 'numeric',
                month: 'short',
                year: 'numeric',
                hour: '2-digit',
                minute: '2-digit'
            });
        }
        
        // Load orders dari localStorage
        function loadOrders() {
            try {
                // 1. Ambil dari admin storage
                const adminOrders = JSON.parse(localStorage.getItem(STORAGE_KEYS.ADMIN_ORDERS) || '[]');
                
                // 2. Ambil dari customer storage (dari e-commerce page)
                const customerOrders = [];
                
                // Cari semua kunci localStorage yang berisi pesanan customer
                for (let i = 0; i < localStorage.length; i++) {
                    const key = localStorage.key(i);
                    if (key.includes('customerOrders') || key.includes('pangsit_order_')) {
                        try {
                            const data = JSON.parse(localStorage.getItem(key));
                            if (data) {
                                if (Array.isArray(data)) {
                                    customerOrders.push(...data);
                                } else {
                                    customerOrders.push(data);
                                }
                            }
                        } catch(e) {
                            console.error('Error parsing customer order:', e);
                        }
                    }
                }
                
                // 3. Gabungkan semua pesanan
                allOrders = [...adminOrders, ...customerOrders];
                
                // 4. Hapus duplikat berdasarkan ID
                const uniqueOrders = [];
                const seenIds = new Set();
                
                allOrders.forEach(order => {
                    if (order && order.id && !seenIds.has(order.id)) {
                        seenIds.add(order.id);
                        uniqueOrders.push(order);
                    }
                });
                
                // 5. Urutkan berdasarkan tanggal terbaru
                uniqueOrders.sort((a, b) => {
                    const timeA = a.timestamp || new Date(a.date || 0).getTime();
                    const timeB = b.timestamp || new Date(b.date || 0).getTime();
                    return timeB - timeA;
                });
                
                // 6. Simpan ke admin storage untuk konsistensi
                localStorage.setItem(STORAGE_KEYS.ADMIN_ORDERS, JSON.stringify(uniqueOrders));
                
                console.log(`✅ Loaded ${uniqueOrders.length} orders`);
                return uniqueOrders;
                
            } catch (error) {
                console.error('Error loading orders:', error);
                return [];
            }
        }
        
        // Save orders ke localStorage
        function saveOrders(orders) {
            try {
                localStorage.setItem(STORAGE_KEYS.ADMIN_ORDERS, JSON.stringify(orders));
                allOrders = orders;
                return true;
            } catch (error) {
                console.error('Error saving orders:', error);
                return false;
            }
        }
        
        // Update order status
        function updateOrderStatus(orderId, newStatus) {
            try {
                const orderIndex = allOrders.findIndex(order => order.id === orderId);
                if (orderIndex === -1) {
                    showNotification('Pesanan tidak ditemukan', 'error');
                    return false;
                }
                
                // Update status
                allOrders[orderIndex].status = newStatus;
                allOrders[orderIndex].updatedAt = new Date().toISOString();
                
                // Save changes
                saveOrders(allOrders);
                
                // Update UI
                renderOrdersTable();
                updateStats();
                
                showNotification(`Status pesanan ${orderId} diubah ke ${getStatusText(newStatus)}`);
                return true;
                
            } catch (error) {
                console.error('Error updating order status:', error);
                showNotification('Gagal mengupdate status', 'error');
                return false;
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
        
        // Update statistics
        function updateStats() {
            const pendingCount = allOrders.filter(o => o.status === 'pending').length;
            const processingCount = allOrders.filter(o => o.status === 'processing').length;
            const completedCount = allOrders.filter(o => o.status === 'completed').length;
            const cancelledCount = allOrders.filter(o => o.status === 'cancelled').length;
            const totalCount = allOrders.length;
            
            document.getElementById('pendingCount').textContent = pendingCount;
            document.getElementById('processingCount').textContent = processingCount;
            document.getElementById('completedCount').textContent = completedCount;
            document.getElementById('totalCount').textContent = totalCount;
        }
        
        // Render orders table
        function renderOrdersTable() {
            const tableBody = document.getElementById('ordersTable');
            const noOrders = document.getElementById('noOrders');
            
            // Filter orders
            filteredOrders = allOrders;
            
            // Apply status filter
            if (currentFilter !== 'all') {
                filteredOrders = filteredOrders.filter(order => order.status === currentFilter);
            }
            
            // Apply search filter
            if (currentSearch) {
                const searchLower = currentSearch.toLowerCase();
                filteredOrders = filteredOrders.filter(order => 
                    order.id.toLowerCase().includes(searchLower) ||
                    (order.customer?.name && order.customer.name.toLowerCase().includes(searchLower)) ||
                    (order.customer?.phone && order.customer.phone.includes(currentSearch)) ||
                    (order.products && order.products.some(p => 
                        p.name && p.name.toLowerCase().includes(searchLower)
                    ))
                );
            }
            
            // Render table
            if (filteredOrders.length === 0) {
                tableBody.innerHTML = '';
                noOrders.style.display = 'block';
                return;
            }
            
            noOrders.style.display = 'none';
            
            let html = '';
            filteredOrders.forEach(order => {
                // Calculate total items
                const totalItems = order.products ? 
                    order.products.reduce((sum, product) => sum + (product.quantity || 1), 0) : 0;
                
                // Status badge
                let statusClass = 'status-pending';
                let statusText = 'Menunggu';
                
                switch(order.status) {
                    case 'processing':
                        statusClass = 'status-processing';
                        statusText = 'Diproses';
                        break;
                    case 'completed':
                        statusClass = 'status-completed';
                        statusText = 'Selesai';
                        break;
                    case 'cancelled':
                        statusClass = 'status-cancelled';
                        statusText = 'Dibatalkan';
                        break;
                }
                
                // Customer info
                const customerName = order.customer?.name || 'Tidak ada nama';
                const customerPhone = order.customer?.phone || 'Tidak ada telepon';
                
                // Products list (max 2 items)
                let productsHtml = '';
                if (order.products && order.products.length > 0) {
                    const productsToShow = order.products.slice(0, 2);
                    productsHtml = productsToShow.map(p => 
                        `${p.name} x${p.quantity || 1}`
                    ).join('<br>');
                    
                    if (order.products.length > 2) {
                        productsHtml += `<br><small>+${order.products.length - 2} lainnya</small>`;
                    }
                } else {
                    productsHtml = 'Tidak ada produk';
                }
                
                html += `
                    <tr>
                        <td class="order-id">${order.id}</td>
                        <td>
                            <div class="customer-name">${customerName}</div>
                            <div class="customer-phone">${customerPhone}</div>
                        </td>
                        <td>${productsHtml}</td>
                        <td>${formatRupiah(order.total || 0)}</td>
                        <td>${order.paymentMethod ? order.paymentMethod.toUpperCase() : 'N/A'}</td>
                        <td>
                            <span class="status-badge ${statusClass}">${statusText}</span>
                        </td>
                        <td>${formatDate(order.timestamp)}</td>
                        <td>
                            <div class="action-buttons">
                                <button class="action-btn btn-view" onclick="viewOrderDetail('${order.id}')" title="Lihat detail">
                                    <i class="fas fa-eye"></i>
                                </button>
                                <button class="action-btn btn-edit" onclick="editOrderStatus('${order.id}')" title="Ubah status">
                                    <i class="fas fa-edit"></i>
                                </button>
                                <button class="action-btn btn-whatsapp" onclick="whatsappCustomer('${order.customer?.phone || ''}')" title="Hubungi WA">
                                    <i class="fab fa-whatsapp"></i>
                                </button>
                            </div>
                        </td>
                    </tr>
                `;
            });
            
            tableBody.innerHTML = html;
        }
        
        // View order detail
        function viewOrderDetail(orderId) {
            const order = allOrders.find(o => o.id === orderId);
            if (!order) {
                showNotification('Pesanan tidak ditemukan', 'error');
                return;
            }
            
            currentOrderId = orderId;
            
            // Format payment method
            let paymentMethodText = order.paymentMethod || 'N/A';
            switch(paymentMethodText.toLowerCase()) {
                case 'gopay': paymentMethodText = 'GoPay'; break;
                case 'ovo': paymentMethodText = 'OVO'; break;
                case 'dana': paymentMethodText = 'DANA'; break;
                case 'qris': paymentMethodText = 'QRIS'; break;
                case 'bca': paymentMethodText = 'Transfer BCA'; break;
                case 'mandiri': paymentMethodText = 'Transfer Mandiri'; break;
                case 'bni': paymentMethodText = 'Transfer BNI'; break;
                case 'bri': paymentMethodText = 'Transfer BRI'; break;
            }
            
            // Products table
            let productsTable = '';
            if (order.products && order.products.length > 0) {
                productsTable = `
                    <table style="width: 100%; border-collapse: collapse; margin-top: 10px;">
                        <thead>
                            <tr style="background-color: var(--light-gray);">
                                <th style="padding: 10px; text-align: left;">Produk</th>
                                <th style="padding: 10px; text-align: center;">Qty</th>
                                <th style="padding: 10px; text-align: right;">Harga</th>
                                <th style="padding: 10px; text-align: right;">Subtotal</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${order.products.map(p => `
                                <tr>
                                    <td style="padding: 10px; border-bottom: 1px solid #eee;">${p.name || 'Produk'}</td>
                                    <td style="padding: 10px; border-bottom: 1px solid #eee; text-align: center;">${p.quantity || 1}</td>
                                    <td style="padding: 10px; border-bottom: 1px solid #eee; text-align: right;">${formatRupiah(p.price || 0)}</td>
                                    <td style="padding: 10px; border-bottom: 1px solid #eee; text-align: right;">${formatRupiah((p.price || 0) * (p.quantity || 1))}</td>
                                </tr>
                            `).join('')}
                        </tbody>
                    </table>
                `;
            } else {
                productsTable = '<p>Tidak ada produk</p>';
            }
            
            const content = document.getElementById('orderDetailContent');
            content.innerHTML = `
                <div class="order-details-grid">
                    <div>
                        <div class="detail-section">
                            <h4><i class="fas fa-info-circle"></i> Informasi Pesanan</h4>
                            <div class="detail-item">
                                <span class="detail-label">ID Pesanan:</span>
                                <span>${order.id}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Tanggal:</span>
                                <span>${formatDate(order.timestamp)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Status Saat Ini:</span>
                                <span><strong>${getStatusText(order.status)}</strong></span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Sumber Data:</span>
                                <span>${order.customer ? 'E-commerce' : 'Admin'}</span>
                            </div>
                        </div>
                        
                        <div class="detail-section">
                            <h4><i class="fas fa-user"></i> Informasi Pelanggan</h4>
                            <div class="detail-item">
                                <span class="detail-label">Nama:</span>
                                <span>${order.customer?.name || 'Tidak ada nama'}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Telepon:</span>
                                <span>${order.customer?.phone || 'Tidak ada telepon'}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Email:</span>
                                <span>${order.customer?.email || 'Tidak ada email'}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Alamat:</span>
                                <span>${order.customer?.address || 'Tidak ada alamat'}</span>
                            </div>
                        </div>
                    </div>
                    
                    <div>
                        <div class="detail-section">
                            <h4><i class="fas fa-credit-card"></i> Informasi Pembayaran</h4>
                            <div class="detail-item">
                                <span class="detail-label">Metode:</span>
                                <span>${paymentMethodText}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Subtotal:</span>
                                <span>${formatRupiah(order.subtotal || 0)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Pengiriman:</span>
                                <span>${formatRupiah(order.shipping || 0)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Pajak:</span>
                                <span>${formatRupiah(order.tax || 0)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Total:</span>
                                <span><strong>${formatRupiah(order.total || 0)}</strong></span>
                            </div>
                        </div>
                        
                        ${order.notes ? `
                        <div class="detail-section">
                            <h4><i class="fas fa-sticky-note"></i> Catatan</h4>
                            <p>${order.notes}</p>
                        </div>
                        ` : ''}
                    </div>
                </div>
                
                <div class="detail-section">
                    <h4><i class="fas fa-box"></i> Detail Produk</h4>
                    ${productsTable}
                </div>
            `;
            
            // Set current status in select
            document.getElementById('statusSelect').value = order.status || 'pending';
            
            // Show modal
            document.getElementById('orderDetailModal').classList.add('active');
        }
        
        // Edit order status
        function editOrderStatus(orderId) {
            const order = allOrders.find(o => o.id === orderId);
            if (order) {
                viewOrderDetail(orderId);
            }
        }
        
        // Hubungi via WhatsApp
        function whatsappCustomer(phone) {
            if (!phone || phone === 'Tidak ada telepon') {
                showNotification('Nomor telepon tidak tersedia', 'warning');
                return;
            }
            
            const message = `Halo, ini admin PANGS!T. Mengenai pesanan Anda.`;
            const whatsappUrl = `https://wa.me/${phone}?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
        }
        
        // Show notification
        function showNotification(message, type = 'success') {
            // Remove existing notification
            const existing = document.querySelector('.notification');
            if (existing) existing.remove();
            
            // Create new notification
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.innerHTML = `
                <i class="fas fa-${type === 'success' ? 'check-circle' : 'exclamation-circle'}"></i>
                ${message}
            `;
            
            document.body.appendChild(notification);
            
            // Auto remove after 5 seconds
            setTimeout(() => notification.remove(), 5000);
        }
        
        // Refresh data
        function refreshData() {
            const refreshBtn = document.getElementById('refreshBtn');
            refreshBtn.classList.add('rotating');
            
            // Check for new orders flag
            const newOrderFlag = localStorage.getItem(STORAGE_KEYS.NEW_ORDER_FLAG);
            let hasNewOrders = false;
            
            if (newOrderFlag) {
                try {
                    const newOrder = JSON.parse(newOrderFlag);
                    console.log('🔔 New order detected:', newOrder.id);
                    hasNewOrders = true;
                    
                    // Clear the flag
                    localStorage.removeItem(STORAGE_KEYS.NEW_ORDER_FLAG);
                } catch(e) {
                    console.error('Error parsing new order flag:', e);
                }
            }
            
            // Load orders
            allOrders = loadOrders();
            
            // Update UI
            renderOrdersTable();
            updateStats();
            
            // Show notification if new orders
            if (hasNewOrders) {
                showNotification('Pesanan baru ditemukan!', 'success');
            }
            
            setTimeout(() => {
                refreshBtn.classList.remove('rotating');
            }, 1000);
        }
        
        // Start auto refresh
        function startAutoRefresh() {
            if (autoRefreshInterval) {
                clearInterval(autoRefreshInterval);
            }
            
            autoRefreshInterval = setInterval(() => {
                refreshData();
            }, 30000); // 30 seconds
            
            console.log('🔄 Auto-refresh aktif (30 detik)');
        }
        
        // Check for new orders from e-commerce page
        function checkForNewOrdersFromEcommerce() {
            // Listen for storage events (from e-commerce page)
            window.addEventListener('storage', function(e) {
                if (e.key === STORAGE_KEYS.NEW_ORDER_FLAG || 
                    e.key.includes('customerOrders') || 
                    e.key.includes('pangsit_order')) {
                    console.log('📦 New order from e-commerce detected');
                    refreshData();
                }
            });
            
            // Also check for localStorage changes within same window
            const originalSetItem = localStorage.setItem;
            localStorage.setItem = function(key, value) {
                originalSetItem.apply(this, arguments);
                
                if (key.includes('customerOrders') || key.includes('pangsit_order')) {
                    console.log('📦 New order saved in localStorage');
                    setTimeout(refreshData, 1000);
                }
            };
        }
        
        // Setup event listeners
        function setupEventListeners() {
            // Refresh button
            document.getElementById('refreshBtn').addEventListener('click', refreshData);
            
            // Filter buttons
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    // Update active state
                    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Update filter
                    currentFilter = this.dataset.filter;
                    renderOrdersTable();
                });
            });
            
            // Search input
            document.getElementById('searchInput').addEventListener('input', function() {
                currentSearch = this.value;
                renderOrdersTable();
            });
            
            // Stat cards filter
            document.querySelectorAll('.stat-card[data-filter]').forEach(card => {
                card.addEventListener('click', function() {
                    const filter = this.getAttribute('data-filter');
                    const filterBtn = document.querySelector(`.filter-btn[data-filter="${filter}"]`);
                    if (filterBtn) {
                        filterBtn.click();
                    }
                });
            });
            
            // Modal close buttons
            document.getElementById('closeModal').addEventListener('click', () => {
                document.getElementById('orderDetailModal').classList.remove('active');
            });
            
            document.getElementById('closeDetailBtn').addEventListener('click', () => {
                document.getElementById('orderDetailModal').classList.remove('active');
            });
            
            document.getElementById('orderDetailModal').addEventListener('click', (e) => {
                if (e.target === document.getElementById('orderDetailModal')) {
                    document.getElementById('orderDetailModal').classList.remove('active');
                }
            });
            
            // Update status button
            document.getElementById('updateStatusBtn').addEventListener('click', () => {
                const newStatus = document.getElementById('statusSelect').value;
                if (currentOrderId && updateOrderStatus(currentOrderId, newStatus)) {
                    document.getElementById('orderDetailModal').classList.remove('active');
                }
            });
            
            // Logout button
            document.getElementById('logoutBtn').addEventListener('click', () => {
                if (confirm('Yakin ingin logout?')) {
                    localStorage.removeItem(STORAGE_KEYS.LOGGED_IN);
                    showNotification('Anda telah logout');
                    setTimeout(() => window.location.reload(), 1000);
                }
            });
        }
        
        // Initialize admin
        function initAdmin() {
            console.log('🚀 Memulai admin panel...');
            
            // Hide login modal
            document.getElementById('loginModal').style.display = 'none';
            
            // Load initial data
            refreshData();
            
            // Start auto refresh
            startAutoRefresh();
            
            // Check for new orders from e-commerce
            checkForNewOrdersFromEcommerce();
            
            // Setup event listeners
            setupEventListeners();
            
            console.log('✅ Admin panel siap digunakan');
        }
        
        // Login function
        function initLogin() {
            const loginForm = document.getElementById('loginForm');
            const loginError = document.getElementById('loginError');
            
            loginForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                
                if (username === ADMIN_CREDENTIALS.username && password === ADMIN_CREDENTIALS.password) {
                    loginError.style.display = 'none';
                    localStorage.setItem(STORAGE_KEYS.LOGGED_IN, 'true');
                    initAdmin();
                } else {
                    loginError.style.display = 'block';
                }
            });
            
            // Auto login for testing
            setTimeout(() => {
                if (localStorage.getItem(STORAGE_KEYS.LOGGED_IN) === 'true') {
                    initAdmin();
                }
            }, 100);
        }
        
        // Check if already logged in
        function checkLogin() {
            const isLoggedIn = localStorage.getItem(STORAGE_KEYS.LOGGED_IN) === 'true';
            
            if (isLoggedIn) {
                initAdmin();
            } else {
                initLogin();
            }
        }
        
        // Start
        document.addEventListener('DOMContentLoaded', checkLogin);
    </script>
</body>
</html>
