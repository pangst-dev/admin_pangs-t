<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin Panel - PANGS!T Store</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
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
        
        .admin-header-content {
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
            font-size: 28px;
            color: var(--primary);
        }
        
        .admin-logo-text {
            font-size: 24px;
            font-weight: 700;
        }
        
        .admin-logo-text span {
            color: var(--primary);
        }
        
        .admin-stats {
            display: flex;
            gap: 20px;
        }
        
        .stat-box {
            background-color: rgba(255, 255, 255, 0.1);
            padding: 12px 20px;
            border-radius: 8px;
            text-align: center;
            min-width: 120px;
        }
        
        .stat-number {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary);
        }
        
        .stat-label {
            font-size: 14px;
            opacity: 0.8;
        }
        
        .admin-controls {
            display: flex;
            gap: 15px;
        }
        
        .btn-admin {
            background-color: var(--primary);
            color: white;
            padding: 10px 20px;
            border-radius: 5px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .btn-admin:hover {
            background-color: var(--primary-dark);
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
        
        /* Main Content */
        .admin-main {
            padding: 30px 0;
            min-height: calc(100vh - 120px);
        }
        
        .admin-tabs {
            display: flex;
            background-color: white;
            border-radius: 10px 10px 0 0;
            overflow: hidden;
            box-shadow: var(--shadow);
        }
        
        .admin-tab {
            padding: 20px 30px;
            cursor: pointer;
            font-weight: 600;
            transition: var(--transition);
            border-bottom: 3px solid transparent;
        }
        
        .admin-tab:hover {
            background-color: var(--light-gray);
        }
        
        .admin-tab.active {
            color: var(--primary);
            border-bottom: 3px solid var(--primary);
            background-color: rgba(255, 107, 53, 0.05);
        }
        
        .admin-tab-content {
            display: none;
            background-color: white;
            padding: 30px;
            border-radius: 0 0 10px 10px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }
        
        .admin-tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        
        /* Orders Table */
        .orders-table-container {
            overflow-x: auto;
        }
        
        .orders-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        
        .orders-table th {
            background-color: var(--secondary);
            color: white;
            padding: 15px;
            text-align: left;
            font-weight: 600;
        }
        
        .orders-table td {
            padding: 15px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .orders-table tr:hover {
            background-color: rgba(255, 107, 53, 0.05);
        }
        
        .order-id {
            font-weight: 700;
            color: var(--secondary);
            font-family: monospace;
        }
        
        .customer-info {
            max-width: 200px;
        }
        
        .customer-name {
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .customer-phone {
            color: var(--gray);
            font-size: 14px;
        }
        
        .order-items {
            max-width: 250px;
        }
        
        .item-list {
            list-style: none;
            font-size: 14px;
        }
        
        .item-list li {
            margin-bottom: 5px;
            padding-bottom: 5px;
            border-bottom: 1px dashed var(--light-gray);
        }
        
        .item-list li:last-child {
            border-bottom: none;
        }
        
        .order-total {
            font-weight: 700;
            color: var(--primary);
            font-size: 18px;
        }
        
        .order-status {
            display: inline-block;
            padding: 6px 15px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
            text-align: center;
            min-width: 120px;
        }
        
        .status-new {
            background-color: #fff3cd;
            color: #856404;
        }
        
        .status-processing {
            background-color: #d1ecf1;
            color: #0c5460;
        }
        
        .status-ready {
            background-color: #d4edda;
            color: #155724;
        }
        
        .status-delivered {
            background-color: #cce5ff;
            color: #004085;
        }
        
        .status-cancelled {
            background-color: #f8d7da;
            color: #721c24;
        }
        
        .order-actions {
            display: flex;
            gap: 8px;
        }
        
        .action-btn {
            padding: 8px 12px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 5px;
            font-size: 14px;
        }
        
        .action-btn.process {
            background-color: var(--info);
            color: white;
        }
        
        .action-btn.ready {
            background-color: var(--success);
            color: white;
        }
        
        .action-btn.deliver {
            background-color: var(--secondary);
            color: white;
        }
        
        .action-btn.cancel {
            background-color: var(--danger);
            color: white;
        }
        
        .action-btn.detail {
            background-color: var(--light-gray);
            color: var(--dark);
        }
        
        .action-btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }
        
        /* Order Detail Modal */
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
            font-size: 24px;
        }
        
        .modal-body {
            padding: 30px;
        }
        
        .order-detail-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .detail-box {
            background-color: var(--light);
            padding: 20px;
            border-radius: 8px;
            border-left: 4px solid var(--primary);
        }
        
        .detail-box h3 {
            color: var(--secondary);
            margin-bottom: 15px;
            font-size: 18px;
        }
        
        .detail-item {
            margin-bottom: 10px;
        }
        
        .detail-label {
            font-weight: 600;
            color: var(--secondary);
            display: block;
            margin-bottom: 3px;
        }
        
        /* Products Management */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .product-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
            border: 1px solid var(--light-gray);
        }
        
        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
        }
        
        .product-img {
            height: 200px;
            width: 100%;
            object-fit: cover;
        }
        
        .product-card-body {
            padding: 20px;
        }
        
        .product-card-title {
            font-size: 20px;
            color: var(--secondary);
            margin-bottom: 10px;
        }
        
        .product-card-price {
            font-size: 22px;
            font-weight: 700;
            color: var(--primary);
            margin-bottom: 15px;
        }
        
        .product-card-actions {
            display: flex;
            gap: 10px;
        }
        
        .btn-edit {
            background-color: var(--info);
            color: white;
        }
        
        .btn-delete {
            background-color: var(--danger);
            color: white;
        }
        
        /* QR Scanner */
        .scanner-container {
            text-align: center;
            padding: 40px 20px;
            background-color: white;
            border-radius: 10px;
            box-shadow: var(--shadow);
            margin-bottom: 30px;
        }
        
        .scanner-title {
            color: var(--secondary);
            margin-bottom: 20px;
            font-size: 24px;
        }
        
        #qr-reader {
            width: 100%;
            max-width: 500px;
            margin: 0 auto;
        }
        
        #qr-reader-results {
            margin-top: 20px;
            padding: 15px;
            background-color: var(--light);
            border-radius: 8px;
            font-family: monospace;
            word-break: break-all;
        }
        
        /* Settings */
        .settings-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        
        .settings-card {
            background-color: white;
            border-radius: 10px;
            padding: 30px;
            box-shadow: var(--shadow);
        }
        
        .settings-card h3 {
            color: var(--secondary);
            margin-bottom: 20px;
            font-size: 20px;
        }
        
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
            border-radius: 6px;
            font-size: 16px;
            transition: var(--transition);
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(255, 107, 53, 0.2);
        }
        
        /* No Data Message */
        .no-data {
            text-align: center;
            padding: 50px 20px;
            color: var(--gray);
        }
        
        .no-data i {
            font-size: 48px;
            margin-bottom: 20px;
            color: var(--light-gray);
        }
        
        /* Responsive */
        @media (max-width: 992px) {
            .admin-header-content {
                flex-direction: column;
                gap: 20px;
                text-align: center;
            }
            
            .admin-stats {
                order: 3;
                width: 100%;
                justify-content: center;
                flex-wrap: wrap;
            }
            
            .admin-tabs {
                overflow-x: auto;
                white-space: nowrap;
            }
            
            .orders-table {
                min-width: 1000px;
            }
        }
        
        @media (max-width: 768px) {
            .admin-tab {
                padding: 15px 20px;
                font-size: 14px;
            }
            
            .admin-tab-content {
                padding: 20px;
            }
            
            .order-actions {
                flex-direction: column;
            }
            
            .modal-content {
                max-height: 95vh;
            }
            
            .modal-body {
                padding: 20px;
            }
            
            .order-detail-grid {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 576px) {
            .stat-box {
                min-width: 100px;
                padding: 10px 15px;
            }
            
            .stat-number {
                font-size: 20px;
            }
            
            .products-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Header Admin -->
    <header class="admin-header">
        <div class="container">
            <div class="admin-header-content">
                <div class="admin-logo">
                    <div class="admin-logo-icon">
                        <i class="fas fa-dumpling"></i>
                    </div>
                    <div class="admin-logo-text">PANGS!T <span>Admin</span></div>
                </div>
                
                <div class="admin-stats">
                    <div class="stat-box">
                        <div class="stat-number" id="totalOrders">0</div>
                        <div class="stat-label">Total Order</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-number" id="newOrders">0</div>
                        <div class="stat-label">Order Baru</div>
                    </div>
                    <div class="stat-box">
                        <div class="stat-number" id="totalRevenue">Rp 0</div>
                        <div class="stat-label">Total Pendapatan</div>
                    </div>
                </div>
                
                <div class="admin-controls">
                    <button class="btn-admin btn-outline" id="refreshBtn">
                        <i class="fas fa-sync-alt"></i> Refresh
                    </button>
                    <button class="btn-admin" id="scanQrBtn">
                        <i class="fas fa-qrcode"></i> Scan QR
                    </button>
                </div>
            </div>
        </div>
    </header>
    
    <!-- Main Content -->
    <main class="admin-main">
        <div class="container">
            <!-- Tabs -->
            <div class="admin-tabs">
                <div class="admin-tab active" data-tab="orders">
                    <i class="fas fa-clipboard-list"></i> Semua Pesanan
                </div>
                <div class="admin-tab" data-tab="new-orders">
                    <i class="fas fa-bell"></i> Pesanan Baru
                </div>
                <div class="admin-tab" data-tab="processing">
                    <i class="fas fa-cog"></i> Sedang Diproses
                </div>
                <div class="admin-tab" data-tab="products">
                    <i class="fas fa-box"></i> Produk
                </div>
                <div class="admin-tab" data-tab="settings">
                    <i class="fas fa-cog"></i> Pengaturan
                </div>
            </div>
            
            <!-- Tab Content: Semua Pesanan -->
            <div class="admin-tab-content active" id="orders-tab">
                <h2>Semua Pesanan</h2>
                <p>Kelola semua pesanan dari pelanggan</p>
                
                <div class="orders-table-container">
                    <table class="orders-table" id="allOrdersTable">
                        <thead>
                            <tr>
                                <th>Order ID</th>
                                <th>Pelanggan</th>
                                <th>Items</th>
                                <th>Total</th>
                                <th>Status</th>
                                <th>Waktu</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="allOrdersBody">
                            <!-- Data akan diisi oleh JavaScript -->
                        </tbody>
                    </table>
                </div>
                
                <div class="no-data" id="noAllOrders">
                    <i class="fas fa-clipboard"></i>
                    <h3>Belum ada pesanan</h3>
                    <p>Semua pesanan akan muncul di sini</p>
                </div>
            </div>
            
            <!-- Tab Content: Pesanan Baru -->
            <div class="admin-tab-content" id="new-orders-tab">
                <h2>Pesanan Baru</h2>
                <p>Pesanan yang masih menunggu konfirmasi</p>
                
                <div class="orders-table-container">
                    <table class="orders-table" id="newOrdersTable">
                        <thead>
                            <tr>
                                <th>Order ID</th>
                                <th>Pelanggan</th>
                                <th>Items</th>
                                <th>Total</th>
                                <th>Waktu</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="newOrdersBody">
                            <!-- Data akan diisi oleh JavaScript -->
                        </tbody>
                    </table>
                </div>
                
                <div class="no-data" id="noNewOrders">
                    <i class="fas fa-bell-slash"></i>
                    <h3>Tidak ada pesanan baru</h3>
                    <p>Pesanan baru akan muncul di sini</p>
                </div>
            </div>
            
            <!-- Tab Content: Sedang Diproses -->
            <div class="admin-tab-content" id="processing-tab">
                <h2>Sedang Diproses</h2>
                <p>Pesanan yang sedang dalam proses pengerjaan</p>
                
                <div class="orders-table-container">
                    <table class="orders-table" id="processingOrdersTable">
                        <thead>
                            <tr>
                                <th>Order ID</th>
                                <th>Pelanggan</th>
                                <th>Items</th>
                                <th>Total</th>
                                <th>Status</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="processingOrdersBody">
                            <!-- Data akan diisi oleh JavaScript -->
                        </tbody>
                    </table>
                </div>
                
                <div class="no-data" id="noProcessingOrders">
                    <i class="fas fa-cog"></i>
                    <h3>Tidak ada pesanan dalam proses</h3>
                    <p>Pesanan yang sedang diproses akan muncul di sini</p>
                </div>
            </div>
            
            <!-- Tab Content: Produk -->
            <div class="admin-tab-content" id="products-tab">
                <h2>Kelola Produk</h2>
                <p>Kelola daftar produk yang dijual</p>
                
                <div style="text-align: right; margin-bottom: 20px;">
                    <button class="btn-admin" id="addProductBtn">
                        <i class="fas fa-plus"></i> Tambah Produk
                    </button>
                </div>
                
                <div class="products-grid" id="productsGrid">
                    <!-- Produk akan diisi oleh JavaScript -->
                </div>
                
                <div class="no-data" id="noProducts">
                    <i class="fas fa-box-open"></i>
                    <h3>Belum ada produk</h3>
                    <p>Tambahkan produk untuk mulai berjualan</p>
                </div>
            </div>
            
            <!-- Tab Content: Pengaturan -->
            <div class="admin-tab-content" id="settings-tab">
                <h2>Pengaturan Toko</h2>
                <p>Atur informasi dan preferensi toko Anda</p>
                
                <div class="settings-grid">
                    <div class="settings-card">
                        <h3>Informasi Toko</h3>
                        <div class="form-group">
                            <label for="storeName">Nama Toko</label>
                            <input type="text" id="storeName" class="form-control" value="PANGS!T Store">
                        </div>
                        <div class="form-group">
                            <label for="storePhone">Telepon</label>
                            <input type="text" id="storePhone" class="form-control" value="+62 831-9524-3139">
                        </div>
                        <div class="form-group">
                            <label for="storeEmail">Email</label>
                            <input type="email" id="storeEmail" class="form-control" value="sitirusmi54@gmail.com">
                        </div>
                        <div class="form-group">
                            <label for="storeAddress">Alamat</label>
                            <textarea id="storeAddress" class="form-control" rows="3">Jl.panongan desa panongan kec panongan kabupaten tangerang</textarea>
                        </div>
                        <button class="btn-admin" id="saveStoreInfo">
                            <i class="fas fa-save"></i> Simpan Info Toko
                        </button>
                    </div>
                    
                    <div class="settings-card">
                        <h3>Pengiriman & Pembayaran</h3>
                        <div class="form-group">
                            <label for="shippingCost">Biaya Pengiriman (Rp)</label>
                            <input type="number" id="shippingCost" class="form-control" value="15000">
                        </div>
                        <div class="form-group">
                            <label for="taxRate">Pajak (%)</label>
                            <input type="number" id="taxRate" class="form-control" value="10" step="0.1">
                        </div>
                        <div class="form-group">
                            <label for="paymentMethods">Metode Pembayaran</label>
                            <div style="margin-top: 10px;">
                                <label style="display: block; margin-bottom: 8px;">
                                    <input type="checkbox" checked> QRIS
                                </label>
                                <label style="display: block; margin-bottom: 8px;">
                                    <input type="checkbox" checked> Bank Transfer
                                </label>
                                <label style="display: block; margin-bottom: 8px;">
                                    <input type="checkbox" checked> GOPAY
                                </label>
                                <label style="display: block; margin-bottom: 8px;">
                                    <input type="checkbox" checked> OVO
                                </label>
                                <label style="display: block; margin-bottom: 8px;">
                                    <input type="checkbox" checked> DANA
                                </label>
                            </div>
                        </div>
                        <button class="btn-admin" id="saveShippingSettings">
                            <i class="fas fa-save"></i> Simpan Pengaturan
                        </button>
                    </div>
                    
                    <div class="settings-card">
                        <h3>Sistem & Backup</h3>
                        <div class="form-group">
                            <label for="autoRefresh">Auto-Refresh Data (detik)</label>
                            <input type="number" id="autoRefresh" class="form-control" value="10" min="5" max="60">
                        </div>
                        <div class="form-group">
                            <label for="notifications">Notifikasi Order Baru</label>
                            <select id="notifications" class="form-control">
                                <option value="enabled" selected>Aktif</option>
                                <option value="disabled">Nonaktif</option>
                            </select>
                        </div>
                        <div style="margin-top: 25px;">
                            <button class="btn-admin" id="exportDataBtn" style="margin-bottom: 10px; width: 100%;">
                                <i class="fas fa-file-export"></i> Ekspor Data Pesanan
                            </button>
                            <button class="btn-admin btn-outline" id="clearDataBtn" style="width: 100%;">
                                <i class="fas fa-trash"></i> Hapus Semua Data
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </main>
    
    <!-- Modal Detail Order -->
    <div class="modal" id="orderDetailModal">
        <div class="modal-content">
            <button class="close-modal" id="closeDetailModal">&times;</button>
            <div class="modal-header">
                <h2 id="modalOrderId">Order #PANG-20250101-001</h2>
                <div class="order-status" id="modalOrderStatus">Status: BARU</div>
            </div>
            <div class="modal-body">
                <div class="order-detail-grid">
                    <div class="detail-box">
                        <h3>Informasi Pelanggan</h3>
                        <div class="detail-item">
                            <span class="detail-label">Nama</span>
                            <span id="customerName">-</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Telepon</span>
                            <span id="customerPhone">-</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Alamat</span>
                            <span id="customerAddress">-</span>
                        </div>
                    </div>
                    
                    <div class="detail-box">
                        <h3>Detail Pesanan</h3>
                        <div class="detail-item">
                            <span class="detail-label">Tanggal</span>
                            <span id="orderDate">-</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Waktu</span>
                            <span id="orderTime">-</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Metode Bayar</span>
                            <span id="paymentMethod">-</span>
                        </div>
                        <div class="detail-item">
                            <span class="detail-label">Catatan</span>
                            <span id="orderNotes">Tidak ada catatan</span>
                        </div>
                    </div>
                    
                    <div class="detail-box">
                        <h3>Status & Aksi</h3>
                        <div class="detail-item">
                            <span class="detail-label">Status Saat Ini</span>
                            <div id="currentStatus">BARU</div>
                        </div>
                        <div style="margin-top: 15px;">
                            <label for="statusSelect">Ubah Status:</label>
                            <select id="statusSelect" class="form-control" style="margin-top: 8px;">
                                <option value="BARU">BARU</option>
                                <option value="PROSES">PROSES</option>
                                <option value="SIAP">SIAP</option>
                                <option value="DIKIRIM">DIKIRIM</option>
                                <option value="SELESAI">SELESAI</option>
                                <option value="BATAL">BATAL</option>
                            </select>
                            <button class="btn-admin" id="updateStatusBtn" style="margin-top: 15px; width: 100%;">
                                <i class="fas fa-sync-alt"></i> Update Status
                            </button>
                        </div>
                    </div>
                </div>
                
                <h3 style="margin-top: 30px; margin-bottom: 15px;">Items Pesanan</h3>
                <table class="orders-table">
                    <thead>
                        <tr>
                            <th>Produk</th>
                            <th>Harga</th>
                            <th>Qty</th>
                            <th>Subtotal</th>
                        </tr>
                    </thead>
                    <tbody id="modalOrderItems">
                        <!-- Items akan diisi oleh JavaScript -->
                    </tbody>
                </table>
                
                <div style="text-align: right; margin-top: 20px;">
                    <div style="font-size: 20px; font-weight: 700; color: var(--primary);">
                        Total: <span id="modalOrderTotal">Rp 0</span>
                    </div>
                </div>
                
                <div style="margin-top: 30px; display: flex; gap: 10px; justify-content: flex-end;">
                    <button class="btn-admin btn-outline" id="closeModalBtn">
                        <i class="fas fa-times"></i> Tutup
                    </button>
                    <button class="btn-admin" id="printInvoiceBtn">
                        <i class="fas fa-print"></i> Cetak Invoice
                    </button>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modal QR Scanner -->
    <div class="modal" id="qrScannerModal">
        <div class="modal-content">
            <button class="close-modal" id="closeQrScanner">&times;</button>
            <div class="modal-body">
                <div class="scanner-container">
                    <h3 class="scanner-title">Scan QR Code Pesanan</h3>
                    <p style="margin-bottom: 20px; color: var(--gray);">
                        Scan QR code dari pelanggan untuk melihat detail pesanan
                    </p>
                    
                    <div id="qr-reader" style="width: 100%;"></div>
                    <div id="qr-reader-results" style="display: none;"></div>
                    
                    <div style="margin-top: 30px; padding: 20px; background-color: var(--light); border-radius: 8px;">
                        <h4 style="color: var(--secondary); margin-bottom: 10px;">Cara Manual:</h4>
                        <p style="margin-bottom: 10px;">Jika scanner tidak bekerja, masukkan kode order secara manual:</p>
                        <div style="display: flex; gap: 10px;">
                            <input type="text" id="manualOrderCode" class="form-control" placeholder="Contoh: PANG-20250101-001">
                            <button class="btn-admin" id="manualSearchBtn">
                                <i class="fas fa-search"></i> Cari
                            </button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <!-- Modal Tambah/Edit Produk -->
    <div class="modal" id="productModal">
        <div class="modal-content">
            <button class="close-modal" id="closeProductModal">&times;</button>
            <div class="modal-header">
                <h2 id="productModalTitle">Tambah Produk Baru</h2>
            </div>
            <div class="modal-body">
                <form id="productForm">
                    <div class="form-group">
                        <label for="productName">Nama Produk</label>
                        <input type="text" id="productName" class="form-control" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="productPrice">Harga (Rp)</label>
                        <input type="number" id="productPrice" class="form-control" required min="1000">
                    </div>
                    
                    <div class="form-group">
                        <label for="productCategory">Kategori</label>
                        <select id="productCategory" class="form-control" required>
                            <option value="pedas">Pedas</option>
                            <option value="original">Original</option>
                            <option value="ayam">Ayam</option>
                            <option value="udang">Udang</option>
                            <option value="spesial">Spesial</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label for="productDescription">Deskripsi</label>
                        <textarea id="productDescription" class="form-control" rows="3" required></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="productImage">URL Gambar</label>
                        <input type="text" id="productImage" class="form-control" placeholder="https://example.com/gambar.jpg">
                        <small style="color: var(--gray);">Masukkan URL gambar atau kosongkan untuk gambar default</small>
                    </div>
                    
                    <div style="margin-top: 30px; display: flex; gap: 10px;">
                        <button type="button" class="btn-admin btn-outline" id="cancelProductBtn">
                            <i class="fas fa-times"></i> Batal
                        </button>
                        <button type="submit" class="btn-admin" id="saveProductBtn">
                            <i class="fas fa-save"></i> Simpan Produk
                        </button>
                    </div>
                    
                    <input type="hidden" id="productId">
                </form>
            </div>
        </div>
    </div>

    <!-- Load QR Scanner Script -->
    <script src="https://unpkg.com/html5-qrcode"></script>
    
    <script>
        // Data Awal
        let orders = JSON.parse(localStorage.getItem('pangsit_admin_orders')) || [];
        let products = JSON.parse(localStorage.getItem('pangsit_admin_products')) || [];
        let storeSettings = JSON.parse(localStorage.getItem('pangsit_store_settings')) || {
            storeName: "PANGS!T Store",
            storePhone: "+62 831-9524-3139",
            storeEmail: "sitirusmi54@gmail.com",
            storeAddress: "Jl.panongan desa panongan kec panongan kabupaten tangerang",
            shippingCost: 15000,
            taxRate: 10,
            autoRefresh: 10,
            notifications: "enabled"
        };

        // DOM Elements
        const allOrdersBody = document.getElementById('allOrdersBody');
        const newOrdersBody = document.getElementById('newOrdersBody');
        const processingOrdersBody = document.getElementById('processingOrdersBody');
        const productsGrid = document.getElementById('productsGrid');
        const totalOrdersElement = document.getElementById('totalOrders');
        const newOrdersElement = document.getElementById('newOrders');
        const totalRevenueElement = document.getElementById('totalRevenue');
        const refreshBtn = document.getElementById('refreshBtn');
        const scanQrBtn = document.getElementById('scanQrBtn');
        const tabs = document.querySelectorAll('.admin-tab');
        const tabContents = document.querySelectorAll('.admin-tab-content');
        const orderDetailModal = document.getElementById('orderDetailModal');
        const qrScannerModal = document.getElementById('qrScannerModal');
        const productModal = document.getElementById('productModal');
        const closeDetailModal = document.getElementById('closeDetailModal');
        const closeQrScanner = document.getElementById('closeQrScanner');
        const closeProductModal = document.getElementById('closeProductModal');
        const statusSelect = document.getElementById('statusSelect');
        const updateStatusBtn = document.getElementById('updateStatusBtn');
        const closeModalBtn = document.getElementById('closeModalBtn');
        const printInvoiceBtn = document.getElementById('printInvoiceBtn');
        const manualSearchBtn = document.getElementById('manualSearchBtn');
        const addProductBtn = document.getElementById('addProductBtn');
        const productForm = document.getElementById('productForm');
        const productModalTitle = document.getElementById('productModalTitle');
        const cancelProductBtn = document.getElementById('cancelProductBtn');
        const saveStoreInfoBtn = document.getElementById('saveStoreInfo');
        const saveShippingSettingsBtn = document.getElementById('saveShippingSettings');
        const exportDataBtn = document.getElementById('exportDataBtn');
        const clearDataBtn = document.getElementById('clearDataBtn');

        // Format Rupiah
        function formatRupiah(amount) {
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(amount);
        }

        // Update Stats
        function updateStats() {
            const totalOrders = orders.length;
            const newOrders = orders.filter(order => order.status === 'BARU' || order.status === 'new').length;
            const totalRevenue = orders.reduce((total, order) => total + order.total, 0);
            
            totalOrdersElement.textContent = totalOrders;
            newOrdersElement.textContent = newOrders;
            totalRevenueElement.textContent = formatRupiah(totalRevenue);
        }

        // Render All Orders
        function renderAllOrders() {
            allOrdersBody.innerHTML = '';
            
            if (orders.length === 0) {
                document.getElementById('noAllOrders').style.display = 'block';
                return;
            }
            
            document.getElementById('noAllOrders').style.display = 'none';
            
            // Urutkan dari yang terbaru
            const sortedOrders = [...orders].sort((a, b) => b.timestamp - a.timestamp);
            
            sortedOrders.forEach(order => {
                const row = document.createElement('tr');
                
                // Tentukan status class
                let statusClass = 'status-new';
                let statusText = 'BARU';
                
                if (order.status === 'processing' || order.status === 'PROSES') {
                    statusClass = 'status-processing';
                    statusText = 'PROSES';
                } else if (order.status === 'ready' || order.status === 'SIAP') {
                    statusClass = 'status-ready';
                    statusText = 'SIAP';
                } else if (order.status === 'delivered' || order.status === 'DIKIRIM') {
                    statusClass = 'status-delivered';
                    statusText = 'DIKIRIM';
                } else if (order.status === 'cancelled' || order.status === 'BATAL') {
                    statusClass = 'status-cancelled';
                    statusText = 'BATAL';
                }
                
                row.innerHTML = `
                    <td>
                        <div class="order-id">${order.id || order.order_id}</div>
                    </td>
                    <td>
                        <div class="customer-info">
                            <div class="customer-name">${order.customer?.name || order.nama || 'Tidak ada nama'}</div>
                            <div class="customer-phone">${order.customer?.phone || order.telp || 'Tidak ada telepon'}</div>
                        </div>
                    </td>
                    <td>
                        <div class="order-items">
                            <ul class="item-list">
                                ${order.products ? order.products.map(item => `
                                    <li>${item.name} x${item.quantity}</li>
                                `).join('') : `<li>${order.items || 'Tidak ada item'}</li>`}
                            </ul>
                        </div>
                    </td>
                    <td>
                        <div class="order-total">${formatRupiah(order.total)}</div>
                    </td>
                    <td>
                        <div class="order-status ${statusClass}">${statusText}</div>
                    </td>
                    <td>
                        ${order.date || ''} ${order.time || ''}
                    </td>
                    <td>
                        <div class="order-actions">
                            <button class="action-btn detail" onclick="viewOrderDetail('${order.id || order.order_id}')">
                                <i class="fas fa-eye"></i> Detail
                            </button>
                        </div>
                    </td>
                `;
                
                allOrdersBody.appendChild(row);
            });
        }

        // Render New Orders
        function renderNewOrders() {
            newOrdersBody.innerHTML = '';
            
            const newOrders = orders.filter(order => 
                order.status === 'BARU' || order.status === 'new' || order.status === 'pending'
            );
            
            if (newOrders.length === 0) {
                document.getElementById('noNewOrders').style.display = 'block';
                return;
            }
            
            document.getElementById('noNewOrders').style.display = 'none';
            
            // Urutkan dari yang terbaru
            const sortedOrders = [...newOrders].sort((a, b) => b.timestamp - a.timestamp);
            
            sortedOrders.forEach(order => {
                const row = document.createElement('tr');
                
                row.innerHTML = `
                    <td>
                        <div class="order-id">${order.id || order.order_id}</div>
                    </td>
                    <td>
                        <div class="customer-info">
                            <div class="customer-name">${order.customer?.name || order.nama || 'Tidak ada nama'}</div>
                            <div class="customer-phone">${order.customer?.phone || order.telp || 'Tidak ada telepon'}</div>
                        </div>
                    </td>
                    <td>
                        <div class="order-items">
                            <ul class="item-list">
                                ${order.products ? order.products.map(item => `
                                    <li>${item.name} x${item.quantity}</li>
                                `).join('') : `<li>${order.items || 'Tidak ada item'}</li>`}
                            </ul>
                        </div>
                    </td>
                    <td>
                        <div class="order-total">${formatRupiah(order.total)}</div>
                    </td>
                    <td>
                        ${order.date || ''} ${order.time || ''}
                    </td>
                    <td>
                        <div class="order-actions">
                            <button class="action-btn process" onclick="updateOrderStatus('${order.id || order.order_id}', 'PROSES')">
                                <i class="fas fa-cog"></i> Proses
                            </button>
                            <button class="action-btn detail" onclick="viewOrderDetail('${order.id || order.order_id}')">
                                <i class="fas fa-eye"></i> Detail
                            </button>
                        </div>
                    </td>
                `;
                
                newOrdersBody.appendChild(row);
            });
        }

        // Render Processing Orders
        function renderProcessingOrders() {
            processingOrdersBody.innerHTML = '';
            
            const processingOrders = orders.filter(order => 
                order.status === 'PROSES' || order.status === 'processing' || 
                order.status === 'SIAP' || order.status === 'ready'
            );
            
            if (processingOrders.length === 0) {
                document.getElementById('noProcessingOrders').style.display = 'block';
                return;
            }
            
            document.getElementById('noProcessingOrders').style.display = 'none';
            
            // Urutkan dari yang terbaru
            const sortedOrders = [...processingOrders].sort((a, b) => b.timestamp - a.timestamp);
            
            sortedOrders.forEach(order => {
                const row = document.createElement('tr');
                
                // Tentukan status
                let statusClass = 'status-processing';
                let statusText = 'PROSES';
                
                if (order.status === 'SIAP' || order.status === 'ready') {
                    statusClass = 'status-ready';
                    statusText = 'SIAP';
                }
                
                row.innerHTML = `
                    <td>
                        <div class="order-id">${order.id || order.order_id}</div>
                    </td>
                    <td>
                        <div class="customer-info">
                            <div class="customer-name">${order.customer?.name || order.nama || 'Tidak ada nama'}</div>
                            <div class="customer-phone">${order.customer?.phone || order.telp || 'Tidak ada telepon'}</div>
                        </div>
                    </td>
                    <td>
                        <div class="order-items">
                            <ul class="item-list">
                                ${order.products ? order.products.map(item => `
                                    <li>${item.name} x${item.quantity}</li>
                                `).join('') : `<li>${order.items || 'Tidak ada item'}</li>`}
                            </ul>
                        </div>
                    </td>
                    <td>
                        <div class="order-total">${formatRupiah(order.total)}</div>
                    </td>
                    <td>
                        <div class="order-status ${statusClass}">${statusText}</div>
                    </td>
                    <td>
                        <div class="order-actions">
                            ${order.status === 'PROSES' || order.status === 'processing' ? `
                                <button class="action-btn ready" onclick="updateOrderStatus('${order.id || order.order_id}', 'SIAP')">
                                    <i class="fas fa-check"></i> Siap
                                </button>
                            ` : `
                                <button class="action-btn deliver" onclick="updateOrderStatus('${order.id || order.order_id}', 'DIKIRIM')">
                                    <i class="fas fa-truck"></i> Kirim
                                </button>
                            `}
                            <button class="action-btn detail" onclick="viewOrderDetail('${order.id || order.order_id}')">
                                <i class="fas fa-eye"></i> Detail
                            </button>
                        </div>
                    </td>
                `;
                
                processingOrdersBody.appendChild(row);
            });
        }

        // Render Products
        function renderProducts() {
            productsGrid.innerHTML = '';
            
            if (products.length === 0) {
                // Load default products if none
                products = [
                    {
                        id: 1,
                        name: "fire silk wonton",
                        price: 20000,
                        image: "foto/fire silk wonton.jpg",
                        description: "Kesan: lembut, pedas aromatik, classy dengan minyak cabai khas Asia.",
                        category: "pedas"
                    },
                    {
                        id: 2,
                        name: "crispy melt deluxe",
                        price: 13000,
                        image: "foto/crispy melt deluxe.jpg",
                        description: "Kesan: garing di luar, lembut & creamy di dalam.",
                        category: "original"
                    },
                    {
                        id: 3,
                        name: "Golden chili crunch",
                        price: 15000,
                        image: "foto/Golden chili crunch.jpg",
                        description: "Kesan: renyah, gurih dengan sentuhan manis-pedas saus khas.",
                        category: "pedas"
                    },
                    {
                        id: 4,
                        name: "bila bila ayam pangsit",
                        price: 10000,
                        image: "foto/bils bila ayam pangsit.jpg",
                        description: "Isi ayam lembut dengan bumbu bawang, merica, dan sedikit sayuran.",
                        category: "ayam"
                    },
                    {
                        id: 5,
                        name: "pangsit kuah mercon",
                        price: 20000,
                        image: "foto/pangsit kuah mercon.jpg",
                        description: "Cocok untuk pangsit kuah. Menggunakan cabai rawit, sambal mercon.",
                        category: "pedas"
                    },
                    {
                        id: 6,
                        name: "pangsit isi tahu",
                        price: 15000,
                        image: "foto/pangsit isi tahu.jpg",
                        description: "Pangsit goreng dengan isian udang utuh yang segar.",
                        category: "udang"
                    }
                ];
                saveProducts();
            }
            
            document.getElementById('noProducts').style.display = 'none';
            
            products.forEach(product => {
                const productCard = document.createElement('div');
                productCard.className = 'product-card';
                
                productCard.innerHTML = `
                    <img src="${product.image || 'foto/default-product.jpg'}" alt="${product.name}" class="product-img" onerror="this.src='foto/default-product.jpg'">
                    <div class="product-card-body">
                        <h3 class="product-card-title">${product.name}</h3>
                        <div class="product-card-price">${formatRupiah(product.price)}</div>
                        <p style="color: var(--gray); margin-bottom: 15px; font-size: 14px;">${product.description.substring(0, 80)}...</p>
                        <div style="display: flex; justify-content: space-between; align-items: center;">
                            <span style="background-color: var(--light-gray); padding: 5px 10px; border-radius: 15px; font-size: 12px;">
                                ${product.category}
                            </span>
                            <div class="product-card-actions">
                                <button class="action-btn btn-edit" onclick="editProduct(${product.id})">
                                    <i class="fas fa-edit"></i>
                                </button>
                                <button class="action-btn btn-delete" onclick="deleteProduct(${product.id})">
                                    <i class="fas fa-trash"></i>
                                </button>
                            </div>
                        </div>
                    </div>
                `;
                
                productsGrid.appendChild(productCard);
            });
        }

        // View Order Detail
        function viewOrderDetail(orderId) {
            const order = orders.find(o => o.id === orderId || o.order_id === orderId);
            if (!order) {
                alert('Order tidak ditemukan!');
                return;
            }
            
            // Set modal content
            document.getElementById('modalOrderId').textContent = `Order #${order.id || order.order_id}`;
            
            // Set status
            let statusText = order.status || 'BARU';
            let statusClass = 'status-new';
            
            if (statusText === 'PROSES' || statusText === 'processing') {
                statusClass = 'status-processing';
            } else if (statusText === 'SIAP' || statusText === 'ready') {
                statusClass = 'status-ready';
            } else if (statusText === 'DIKIRIM' || statusText === 'delivered') {
                statusClass = 'status-delivered';
            } else if (statusText === 'BATAL' || statusText === 'cancelled') {
                statusClass = 'status-cancelled';
            }
            
            document.getElementById('modalOrderStatus').className = `order-status ${statusClass}`;
            document.getElementById('modalOrderStatus').textContent = statusText;
            document.getElementById('currentStatus').textContent = statusText;
            
            // Set customer info
            document.getElementById('customerName').textContent = order.customer?.name || order.nama || '-';
            document.getElementById('customerPhone').textContent = order.customer?.phone || order.telp || '-';
            document.getElementById('customerAddress').textContent = order.customer?.address || order.alamat || '-';
            
            // Set order info
            document.getElementById('orderDate').textContent = order.date || '-';
            document.getElementById('orderTime').textContent = order.time || '-';
            document.getElementById('paymentMethod').textContent = order.paymentMethod || '-';
            document.getElementById('orderNotes').textContent = order.notes || order.catatan || 'Tidak ada catatan';
            
            // Set order items
            const itemsBody = document.getElementById('modalOrderItems');
            itemsBody.innerHTML = '';
            
            if (order.products) {
                order.products.forEach(item => {
                    const row = document.createElement('tr');
                    row.innerHTML = `
                        <td>${item.name}</td>
                        <td>${formatRupiah(item.price)}</td>
                        <td>${item.quantity}</td>
                        <td>${formatRupiah(item.price * item.quantity)}</td>
                    `;
                    itemsBody.appendChild(row);
                });
            } else if (order.items) {
                const row = document.createElement('tr');
                row.innerHTML = `
                    <td>${order.items}</td>
                    <td>-</td>
                    <td>1</td>
                    <td>${formatRupiah(order.total)}</td>
                `;
                itemsBody.appendChild(row);
            }
            
            // Set total
            document.getElementById('modalOrderTotal').textContent = formatRupiah(order.total);
            
            // Set current status in select
            document.getElementById('statusSelect').value = statusText;
            
            // Store current order ID
            orderDetailModal.dataset.currentOrderId = order.id || order.order_id;
            
            // Show modal
            orderDetailModal.classList.add('active');
        }

        // Update Order Status
        function updateOrderStatus(orderId, newStatus) {
            const orderIndex = orders.findIndex(o => o.id === orderId || o.order_id === orderId);
            
            if (orderIndex === -1) {
                alert('Order tidak ditemukan!');
                return;
            }
            
            // Update status
            orders[orderIndex].status = newStatus;
            orders[orderIndex].timestamp = Date.now();
            
            // Save to localStorage
            saveOrders();
            
            // Update display
            renderAllOrders();
            renderNewOrders();
            renderProcessingOrders();
            updateStats();
            
            // Show notification
            showNotification(`Status order ${orderId} berhasil diubah menjadi ${newStatus}`, 'success');
            
            // If modal is open, update it
            if (orderDetailModal.classList.contains('active') && 
                orderDetailModal.dataset.currentOrderId === orderId) {
                viewOrderDetail(orderId);
            }
        }

        // Save Orders to localStorage
        function saveOrders() {
            localStorage.setItem('pangsit_admin_orders', JSON.stringify(orders));
        }

        // Save Products to localStorage
        function saveProducts() {
            localStorage.setItem('pangsit_admin_products', JSON.stringify(products));
        }

        // Save Settings to localStorage
        function saveSettings() {
            localStorage.setItem('pangsit_store_settings', JSON.stringify(storeSettings));
        }

        // Show Notification
        function showNotification(message, type = 'success') {
            // Remove existing notification
            const existingNotification = document.querySelector('.admin-notification');
            if (existingNotification) {
                existingNotification.remove();
            }
            
            // Create notification element
            const notification = document.createElement('div');
            notification.className = `admin-notification ${type}`;
            notification.textContent = message;
            notification.style.cssText = `
                position: fixed;
                top: 20px;
                right: 20px;
                background-color: ${type === 'success' ? 'var(--success)' : 
                                 type === 'error' ? 'var(--danger)' : 
                                 type === 'warning' ? 'var(--warning)' : 'var(--info)'};
                color: white;
                padding: 15px 25px;
                border-radius: 8px;
                box-shadow: 0 5px 15px rgba(0,0,0,0.2);
                z-index: 2000;
                animation: slideIn 0.3s ease;
            `;
            
            document.body.appendChild(notification);
            
            // Remove notification after 3 seconds
            setTimeout(() => {
                notification.style.animation = 'slideOut 0.3s ease';
                setTimeout(() => {
                    notification.remove();
                }, 300);
            }, 3000);
        }

        // Load Settings
        function loadSettings() {
            if (storeSettings) {
                document.getElementById('storeName').value = storeSettings.storeName;
                document.getElementById('storePhone').value = storeSettings.storePhone;
                document.getElementById('storeEmail').value = storeSettings.storeEmail;
                document.getElementById('storeAddress').value = storeSettings.storeAddress;
                document.getElementById('shippingCost').value = storeSettings.shippingCost;
                document.getElementById('taxRate').value = storeSettings.taxRate;
                document.getElementById('autoRefresh').value = storeSettings.autoRefresh;
                document.getElementById('notifications').value = storeSettings.notifications;
            }
        }

        // Export Data
        function exportData() {
            const data = {
                orders: orders,
                products: products,
                settings: storeSettings,
                exportDate: new Date().toISOString()
            };
            
            const dataStr = JSON.stringify(data, null, 2);
            const dataBlob = new Blob([dataStr], { type: 'application/json' });
            const url = URL.createObjectURL(dataBlob);
            
            const a = document.createElement('a');
            a.href = url;
            a.download = `pangsit-backup-${new Date().toISOString().split('T')[0]}.json`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            
            showNotification('Data berhasil diekspor!', 'success');
        }

        // Clear Data
        function clearData() {
            if (confirm('Apakah Anda yakin ingin menghapus semua data? Tindakan ini tidak dapat dibatalkan.')) {
                localStorage.removeItem('pangsit_admin_orders');
                localStorage.removeItem('pangsit_admin_products');
                localStorage.removeItem('pangsit_store_settings');
                
                orders = [];
                products = [];
                storeSettings = {
                    storeName: "PANGS!T Store",
                    storePhone: "+62 831-9524-3139",
                    storeEmail: "sitirusmi54@gmail.com",
                    storeAddress: "Jl.panongan desa panongan kec panongan kabupaten tangerang",
                    shippingCost: 15000,
                    taxRate: 10,
                    autoRefresh: 10,
                    notifications: "enabled"
                };
                
                loadSettings();
                renderAllOrders();
                renderNewOrders();
                renderProcessingOrders();
                renderProducts();
                updateStats();
                
                showNotification('Semua data telah dihapus!', 'success');
            }
        }

        // Add/Edit Product
        function openProductModal(productId = null) {
            if (productId) {
                // Edit mode
                const product = products.find(p => p.id === productId);
                if (!product) return;
                
                productModalTitle.textContent = 'Edit Produk';
                document.getElementById('productId').value = product.id;
                document.getElementById('productName').value = product.name;
                document.getElementById('productPrice').value = product.price;
                document.getElementById('productCategory').value = product.category;
                document.getElementById('productDescription').value = product.description;
                document.getElementById('productImage').value = product.image || '';
            } else {
                // Add mode
                productModalTitle.textContent = 'Tambah Produk Baru';
                productForm.reset();
                document.getElementById('productId').value = '';
            }
            
            productModal.classList.add('active');
        }

        function saveProduct(e) {
            e.preventDefault();
            
            const productId = document.getElementById('productId').value;
            const productName = document.getElementById('productName').value;
            const productPrice = parseInt(document.getElementById('productPrice').value);
            const productCategory = document.getElementById('productCategory').value;
            const productDescription = document.getElementById('productDescription').value;
            const productImage = document.getElementById('productImage').value;
            
            if (productId) {
                // Update existing product
                const index = products.findIndex(p => p.id === parseInt(productId));
                if (index !== -1) {
                    products[index] = {
                        ...products[index],
                        name: productName,
                        price: productPrice,
                        category: productCategory,
                        description: productDescription,
                        image: productImage || products[index].image
                    };
                }
            } else {
                // Add new product
                const newProduct = {
                    id: products.length > 0 ? Math.max(...products.map(p => p.id)) + 1 : 1,
                    name: productName,
                    price: productPrice,
                    category: productCategory,
                    description: productDescription,
                    image: productImage || 'foto/default-product.jpg'
                };
                products.push(newProduct);
            }
            
            saveProducts();
            renderProducts();
            productModal.classList.remove('active');
            
            showNotification(`Produk ${productName} berhasil disimpan!`, 'success');
        }

        function editProduct(productId) {
            openProductModal(productId);
        }

        function deleteProduct(productId) {
            if (confirm('Apakah Anda yakin ingin menghapus produk ini?')) {
                products = products.filter(p => p.id !== productId);
                saveProducts();
                renderProducts();
                showNotification('Produk berhasil dihapus!', 'success');
            }
        }

        // QR Scanner
        function openQrScanner() {
            qrScannerModal.classList.add('active');
            
            // Initialize QR Scanner
            if (window.Html5Qrcode) {
                const html5QrCode = new Html5Qrcode("qr-reader");
                
                const qrCodeSuccessCallback = (decodedText, decodedResult) => {
                    // Handle the scanned code
                    html5QrCode.stop().then(() => {
                        qrScannerModal.classList.remove('active');
                        
                        // Look for order with this ID
                        const order = orders.find(o => 
                            o.id === decodedText || 
                            o.order_id === decodedText ||
                            decodedText.includes(o.id) || 
                            decodedText.includes(o.order_id)
                        );
                        
                        if (order) {
                            viewOrderDetail(order.id || order.order_id);
                        } else {
                            alert('Order tidak ditemukan. Kode: ' + decodedText);
                        }
                    });
                };
                
                const config = { 
                    fps: 10, 
                    qrbox: { width: 250, height: 250 } 
                };
                
                html5QrCode.start(
                    { facingMode: "environment" }, 
                    config, 
                    qrCodeSuccessCallback
                ).catch(err => {
                    console.error("QR Scanner error:", err);
                });
                
                // Store scanner instance to stop later
                qrScannerModal.dataset.scanner = html5QrCode;
            }
        }

        // Check for new orders from customer website
        function checkForNewOrders() {
            // Check localStorage for orders from customer site
            try {
                const customerOrders = JSON.parse(localStorage.getItem('pangsit_cloud_orders')) || [];
                
                // Add any new orders to admin orders
                customerOrders.forEach(customerOrder => {
                    // Check if order already exists
                    const exists = orders.some(o => o.order_id === customerOrder.order_id);
                    
                    if (!exists) {
                        // Convert customer order format to admin order format
                        const newOrder = {
                            id: customerOrder.order_id,
                            order_id: customerOrder.order_id,
                            nama: customerOrder.nama,
                            telp: customerOrder.telp,
                            alamat: customerOrder.alamat,
                            items: customerOrder.items,
                            total: customerOrder.total,
                            date: customerOrder.waktu.split(', ')[0],
                            time: customerOrder.waktu.split(', ')[1] || '',
                            status: customerOrder.status || 'BARU',
                            timestamp: Date.now()
                        };
                        
                        orders.push(newOrder);
                        
                        // Show notification for new order
                        if (storeSettings.notifications === 'enabled') {
                            showNotification(`Pesanan baru: ${newOrder.nama} - ${formatRupiah(newOrder.total)}`, 'success');
                            
                            // Play notification sound if allowed
                            if (typeof Audio !== 'undefined') {
                                const audio = new Audio('https://assets.mixkit.co/sfx/preview/mixkit-alarm-digital-clock-beep-989.mp3');
                                audio.volume = 0.3;
                                audio.play().catch(e => console.log('Audio error:', e));
                            }
                        }
                    }
                });
                
                // Save and update
                if (customerOrders.length > 0) {
                    saveOrders();
                    renderAllOrders();
                    renderNewOrders();
                    updateStats();
                }
                
            } catch (error) {
                console.error('Error checking for new orders:', error);
            }
        }

        // Initialize
        function init() {
            // Load data
            if (localStorage.getItem('pangsit_admin_orders')) {
                orders = JSON.parse(localStorage.getItem('pangsit_admin_orders'));
            }
            
            if (localStorage.getItem('pangsit_admin_products')) {
                products = JSON.parse(localStorage.getItem('pangsit_admin_products'));
            }
            
            if (localStorage.getItem('pangsit_store_settings')) {
                storeSettings = JSON.parse(localStorage.getItem('pangsit_store_settings'));
            }
            
            // Initial render
            renderAllOrders();
            renderNewOrders();
            renderProcessingOrders();
            renderProducts();
            updateStats();
            loadSettings();
            
            // Tab switching
            tabs.forEach(tab => {
                tab.addEventListener('click', () => {
                    const tabId = tab.getAttribute('data-tab');
                    
                    // Update active tab
                    tabs.forEach(t => t.classList.remove('active'));
                    tab.classList.add('active');
                    
                    // Show corresponding content
                    tabContents.forEach(content => {
                        content.classList.remove('active');
                        if (content.id === `${tabId}-tab`) {
                            content.classList.add('active');
                        }
                    });
                });
            });
            
            // Refresh button
            refreshBtn.addEventListener('click', () => {
                renderAllOrders();
                renderNewOrders();
                renderProcessingOrders();
                updateStats();
                checkForNewOrders();
                showNotification('Data diperbarui!', 'success');
            });
            
            // QR Scanner button
            scanQrBtn.addEventListener('click', openQrScanner);
            
            // Modal close buttons
            closeDetailModal.addEventListener('click', () => {
                orderDetailModal.classList.remove('active');
            });
            
            closeQrScanner.addEventListener('click', () => {
                qrScannerModal.classList.remove('active');
                // Stop scanner if running
                if (qrScannerModal.dataset.scanner) {
                    qrScannerModal.dataset.scanner.stop();
                }
            });
            
            closeProductModal.addEventListener('click', () => {
                productModal.classList.remove('active');
            });
            
            // Update status button
            updateStatusBtn.addEventListener('click', () => {
                const orderId = orderDetailModal.dataset.currentOrderId;
                const newStatus = document.getElementById('statusSelect').value;
                
                if (orderId) {
                    updateOrderStatus(orderId, newStatus);
                }
            });
            
            closeModalBtn.addEventListener('click', () => {
                orderDetailModal.classList.remove('active');
            });
            
            // Print invoice button
            printInvoiceBtn.addEventListener('click', () => {
                const orderId = orderDetailModal.dataset.currentOrderId;
                const order = orders.find(o => o.id === orderId || o.order_id === orderId);
                
                if (order) {
                    // Create printable invoice
                    const invoiceWindow = window.open('', '_blank');
                    invoiceWindow.document.write(`
                        <!DOCTYPE html>
                        <html>
                        <head>
                            <title>Invoice ${order.id || order.order_id}</title>
                            <style>
                                body { font-family: Arial, sans-serif; margin: 30px; }
                                .invoice-header { text-align: center; margin-bottom: 30px; border-bottom: 2px solid #ff6b35; padding-bottom: 20px; }
                                .invoice-title { font-size: 28px; color: #ff6b35; font-weight: bold; }
                                .invoice-table { width: 100%; border-collapse: collapse; margin: 20px 0; }
                                .invoice-table th, .invoice-table td { padding: 12px; border: 1px solid #ddd; }
                                .invoice-table th { background-color: #f5f5f5; }
                                .invoice-total { float: right; width: 300px; margin-top: 20px; }
                                @media print {
                                    body { margin: 0; }
                                    .no-print { display: none; }
                                }
                            </style>
                        </head>
                        <body>
                            <div class="invoice-header">
                                <div class="invoice-title">PANGS!T STORE</div>
                                <p>Jl.panongan desa panongan kec panongan kabupaten tangerang</p>
                                <p>Telp: +62 831-9524-3139 | Email: sitirusmi54@gmail.com</p>
                            </div>
                            
                            <div style="display: flex; justify-content: space-between; margin-bottom: 20px;">
                                <div>
                                    <h3>INVOICE</h3>
                                    <p><strong>No:</strong> ${order.id || order.order_id}</p>
                                    <p><strong>Tanggal:</strong> ${order.date || ''}</p>
                                    <p><strong>Waktu:</strong> ${order.time || ''}</p>
                                </div>
                                <div>
                                    <h3>Kepada:</h3>
                                    <p><strong>Nama:</strong> ${order.customer?.name || order.nama || ''}</p>
                                    <p><strong>Telp:</strong> ${order.customer?.phone || order.telp || ''}</p>
                                    <p><strong>Alamat:</strong> ${order.customer?.address || order.alamat || ''}</p>
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
                                    ${order.products ? order.products.map(item => `
                                        <tr>
                                            <td>${item.name}</td>
                                            <td>${formatRupiah(item.price)}</td>
                                            <td>${item.quantity}</td>
                                            <td>${formatRupiah(item.price * item.quantity)}</td>
                                        </tr>
                                    `).join('') : `
                                        <tr>
                                            <td>${order.items || ''}</td>
                                            <td>-</td>
                                            <td>1</td>
                                            <td>${formatRupiah(order.total)}</td>
                                        </tr>
                                    `}
                                </tbody>
                            </table>
                            
                            <div class="invoice-total">
                                <div style="display: flex; justify-content: space-between; margin-bottom: 10px;">
                                    <span>Subtotal:</span>
                                    <span>${formatRupiah(order.total)}</span>
                                </div>
                                <div style="display: flex; justify-content: space-between; font-weight: bold; font-size: 20px; border-top: 2px solid #ff6b35; padding-top: 10px; margin-top: 10px;">
                                    <span>TOTAL:</span>
                                    <span style="color: #ff6b35;">${formatRupiah(order.total)}</span>
                                </div>
                            </div>
                            <div style="clear: both;"></div>
                            
                            <div style="margin-top: 40px; padding: 20px; background-color: #f8f9fa; border-radius: 5px;">
                                <p><strong>Status:</strong> ${order.status || 'BARU'}</p>
                                <p><strong>Catatan:</strong> ${order.notes || order.catatan || 'Tidak ada catatan'}</p>
                            </div>
                            
                            <div style="margin-top: 40px; text-align: center; color: #666; font-size: 14px;">
                                <p>Terima kasih telah berbelanja di PANGS!T STORE</p>
                                <p>Invoice ini dicetak pada: ${new Date().toLocaleString('id-ID')}</p>
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
                    `);
                    invoiceWindow.document.close();
                }
            });
            
            // Manual search for order
            manualSearchBtn.addEventListener('click', () => {
                const orderCode = document.getElementById('manualOrderCode').value;
                if (orderCode) {
                    const order = orders.find(o => 
                        o.id === orderCode || 
                        o.order_id === orderCode ||
                        o.id.includes(orderCode) || 
                        o.order_id.includes(orderCode)
                    );
                    
                    if (order) {
                        qrScannerModal.classList.remove('active');
                        viewOrderDetail(order.id || order.order_id);
                    } else {
                        alert('Order tidak ditemukan!');
                    }
                }
            });
            
            // Product management
            addProductBtn.addEventListener('click', () => openProductModal());
            productForm.addEventListener('submit', saveProduct);
            cancelProductBtn.addEventListener('click', () => {
                productModal.classList.remove('active');
            });
            
            // Settings
            saveStoreInfoBtn.addEventListener('click', () => {
                storeSettings.storeName = document.getElementById('storeName').value;
                storeSettings.storePhone = document.getElementById('storePhone').value;
                storeSettings.storeEmail = document.getElementById('storeEmail').value;
                storeSettings.storeAddress = document.getElementById('storeAddress').value;
                
                saveSettings();
                showNotification('Informasi toko berhasil disimpan!', 'success');
            });
            
            saveShippingSettingsBtn.addEventListener('click', () => {
                storeSettings.shippingCost = parseInt(document.getElementById('shippingCost').value);
                storeSettings.taxRate = parseFloat(document.getElementById('taxRate').value);
                
                saveSettings();
                showNotification('Pengaturan pengiriman berhasil disimpan!', 'success');
            });
            
            exportDataBtn.addEventListener('click', exportData);
            clearDataBtn.addEventListener('click', clearData);
            
            // Auto-refresh
            const autoRefreshInterval = storeSettings.autoRefresh * 1000;
            setInterval(() => {
                checkForNewOrders();
            }, autoRefreshInterval);
            
            // Check for new orders immediately
            setTimeout(checkForNewOrders, 2000);
            
            // Add notification styles
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
            
            console.log('✅ Admin Panel PANGS!T siap digunakan!');
        }

        // Global functions for HTML onclick
        window.viewOrderDetail = viewOrderDetail;
        window.updateOrderStatus = updateOrderStatus;
        window.editProduct = editProduct;
        window.deleteProduct = deleteProduct;

        // Initialize when page loads
        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
