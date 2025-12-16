<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Admin PANGS!T - Monitoring Pesanan Real-Time</title>
    <!-- Gunakan CDN untuk semua resources -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Segoe+UI:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* ==================== RESET & VARIABLES ==================== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
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
        
        body {
            font-family: 'Segoe UI', system-ui, sans-serif;
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
        
        /* ==================== LOGIN PAGE ==================== */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: linear-gradient(135deg, var(--secondary) 0%, #1a1c2f 100%);
            padding: 20px;
        }
        
        .login-box {
            background-color: white;
            border-radius: 15px;
            padding: 40px;
            width: 100%;
            max-width: 400px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        .login-logo {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .login-logo .logo-icon {
            color: var(--primary);
            font-size: 48px;
            margin-bottom: 15px;
        }
        
        .login-logo .logo-text {
            font-size: 28px;
            font-weight: 700;
            color: var(--secondary);
        }
        
        .login-logo .logo-text span {
            color: var(--primary);
        }
        
        .login-title {
            text-align: center;
            margin-bottom: 30px;
        }
        
        .login-title h2 {
            color: var(--secondary);
            margin-bottom: 10px;
        }
        
        .login-title p {
            color: var(--gray);
        }
        
        .login-form .form-group {
            margin-bottom: 20px;
        }
        
        .login-form label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary);
        }
        
        .login-form input {
            width: 100%;
            padding: 14px;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            font-size: 16px;
            transition: var(--transition);
        }
        
        .login-form input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(255, 107, 53, 0.1);
        }
        
        .login-btn {
            width: 100%;
            padding: 16px;
            margin-top: 10px;
            font-size: 16px;
            font-weight: 600;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .login-btn:hover {
            background: var(--primary-dark);
        }
        
        .login-error {
            color: var(--danger);
            text-align: center;
            margin-top: 15px;
            font-size: 14px;
            display: none;
        }
        
        /* ==================== ADMIN DASHBOARD ==================== */
        #adminPage {
            display: none;
            animation: fadeIn 0.5s ease;
        }
        
        .admin-header {
            background: linear-gradient(135deg, var(--secondary) 0%, #1a1c2f 100%);
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
            color: var(--primary);
            font-size: 24px;
        }
        
        .admin-logo-text {
            font-size: 22px;
            font-weight: 700;
        }
        
        .admin-logo-text span {
            color: var(--primary);
        }
        
        .admin-user {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .admin-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 600;
            font-size: 18px;
        }
        
        .logout-btn {
            background-color: transparent;
            border: 1px solid rgba(255, 255, 255, 0.3);
            color: white;
            padding: 8px 16px;
            border-radius: 5px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 500;
        }
        
        .logout-btn:hover {
            background-color: rgba(255, 255, 255, 0.1);
            transform: translateY(-2px);
        }
        
        .admin-main {
            min-height: calc(100vh - 160px);
            padding: 30px 0;
        }
        
        .admin-title {
            margin-bottom: 30px;
        }
        
        .admin-title h1 {
            font-size: 32px;
            color: var(--secondary);
            margin-bottom: 10px;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .live-badge {
            background: var(--danger);
            color: white;
            font-size: 12px;
            padding: 5px 12px;
            border-radius: 20px;
            animation: pulse 1.5s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.6; }
            100% { opacity: 1; }
        }
        
        /* ==================== STATS CARDS ==================== */
        .stats-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .stat-card {
            background-color: white;
            border-radius: 12px;
            padding: 25px;
            box-shadow: var(--shadow);
            display: flex;
            align-items: center;
            gap: 20px;
            transition: var(--transition);
            cursor: pointer;
            border: 2px solid transparent;
        }
        
        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
            border-color: var(--primary);
        }
        
        .stat-icon {
            width: 60px;
            height: 60px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            color: white;
        }
        
        .stat-icon.pending {
            background: linear-gradient(135deg, var(--warning) 0%, #e0a800 100%);
        }
        
        .stat-icon.processing {
            background: linear-gradient(135deg, var(--info) 0%, #138496 100%);
        }
        
        .stat-icon.completed {
            background: linear-gradient(135deg, var(--success) 0%, #1e7e34 100%);
        }
        
        .stat-icon.total {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
        }
        
        .stat-info h3 {
            font-size: 32px;
            margin-bottom: 5px;
            color: var(--secondary);
        }
        
        .stat-info p {
            color: var(--gray);
            font-size: 14px;
        }
        
        /* ==================== CONTROLS ==================== */
        .admin-controls {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 25px;
            flex-wrap: wrap;
            gap: 15px;
            background-color: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: var(--shadow);
        }
        
        .search-box {
            position: relative;
            flex: 1;
            max-width: 400px;
        }
        
        .search-box input {
            width: 100%;
            padding: 12px 20px 12px 45px;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            font-size: 16px;
            transition: var(--transition);
        }
        
        .search-box input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(255, 107, 53, 0.1);
        }
        
        .search-icon {
            position: absolute;
            left: 15px;
            top: 50%;
            transform: translateY(-50%);
            color: var(--gray);
        }
        
        .filter-controls {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }
        
        .filter-btn {
            padding: 10px 20px;
            background-color: white;
            border: 1px solid var(--light-gray);
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        
        .filter-btn:hover {
            background-color: var(--light-gray);
        }
        
        .filter-btn.active {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            border-color: var(--primary);
        }
        
        /* ==================== ORDERS TABLE ==================== */
        .orders-table-container {
            background-color: white;
            border-radius: 12px;
            box-shadow: var(--shadow);
            overflow: hidden;
            margin-bottom: 40px;
        }
        
        .table-header {
            padding: 20px;
            border-bottom: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .table-header h3 {
            color: var(--secondary);
            font-size: 18px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .refresh-btn {
            background: none;
            border: 1px solid var(--light-gray);
            padding: 8px 16px;
            border-radius: 6px;
            cursor: pointer;
            transition: var(--transition);
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 500;
        }
        
        .refresh-btn:hover {
            background-color: var(--light-gray);
        }
        
        .refresh-btn.rotating {
            animation: rotate 1s linear infinite;
        }
        
        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }
        
        .orders-table {
            width: 100%;
            border-collapse: collapse;
        }
        
        .orders-table thead {
            background-color: var(--light-gray);
        }
        
        .orders-table th {
            padding: 18px 15px;
            text-align: left;
            font-weight: 600;
            color: var(--secondary);
            font-size: 15px;
            border-bottom: 2px solid var(--light-gray);
        }
        
        .orders-table tbody tr {
            border-bottom: 1px solid var(--light-gray);
            transition: var(--transition);
        }
        
        .orders-table tbody tr:hover {
            background-color: rgba(255, 107, 53, 0.05);
        }
        
        .orders-table tbody tr.new-order {
            animation: highlightNew 2s ease;
            background-color: rgba(255, 107, 53, 0.1);
        }
        
        @keyframes highlightNew {
            0% { background-color: rgba(255, 107, 53, 0.3); }
            100% { background-color: rgba(255, 107, 53, 0.1); }
        }
        
        .orders-table td {
            padding: 15px;
            vertical-align: top;
        }
        
        .order-id {
            font-weight: 600;
            color: var(--secondary);
        }
        
        .customer-info .customer-name {
            font-weight: 600;
            margin-bottom: 5px;
            color: var(--secondary);
        }
        
        .customer-info .customer-phone {
            color: var(--gray);
            font-size: 14px;
        }
        
        .product-list {
            list-style: none;
            max-height: 100px;
            overflow-y: auto;
            padding-right: 5px;
        }
        
        .product-list::-webkit-scrollbar {
            width: 4px;
        }
        
        .product-list::-webkit-scrollbar-track {
            background: var(--light-gray);
            border-radius: 4px;
        }
        
        .product-list::-webkit-scrollbar-thumb {
            background: var(--primary);
            border-radius: 4px;
        }
        
        .product-list li {
            margin-bottom: 8px;
            padding-bottom: 8px;
            border-bottom: 1px dashed var(--light-gray);
            font-size: 14px;
        }
        
        .product-list li:last-child {
            margin-bottom: 0;
            padding-bottom: 0;
            border-bottom: none;
        }
        
        /* ==================== STATUS BADGES ==================== */
        .status-badge {
            display: inline-block;
            padding: 6px 12px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            min-width: 100px;
            text-align: center;
        }
        
        .status-pending {
            background-color: rgba(255, 193, 7, 0.15);
            color: #b38b00;
            border: 1px solid rgba(255, 193, 7, 0.3);
        }
        
        .status-processing {
            background-color: rgba(23, 162, 184, 0.15);
            color: #0c5460;
            border: 1px solid rgba(23, 162, 184, 0.3);
        }
        
        .status-completed {
            background-color: rgba(40, 167, 69, 0.15);
            color: #155724;
            border: 1px solid rgba(40, 167, 69, 0.3);
        }
        
        .status-cancelled {
            background-color: rgba(220, 53, 69, 0.15);
            color: #721c24;
            border: 1px solid rgba(220, 53, 69, 0.3);
        }
        
        /* ==================== ACTION BUTTONS ==================== */
        .action-buttons {
            display: flex;
            gap: 8px;
        }
        
        .action-btn {
            width: 36px;
            height: 36px;
            border-radius: 6px;
            display: flex;
            align-items: center;
            justify-content: center;
            border: none;
            cursor: pointer;
            transition: var(--transition);
            color: white;
            font-size: 14px;
        }
        
        .action-btn.view {
            background: linear-gradient(135deg, var(--info) 0%, #138496 100%);
        }
        
        .action-btn.edit {
            background: linear-gradient(135deg, var(--warning) 0%, #e0a800 100%);
        }
        
        .action-btn.delete {
            background: linear-gradient(135deg, var(--danger) 0%, #c82333 100%);
        }
        
        .action-btn:hover {
            opacity: 0.9;
            transform: scale(1.05);
        }
        
        /* ==================== NO ORDERS MESSAGE ==================== */
        .no-orders {
            text-align: center;
            padding: 60px 20px;
            color: var(--gray);
        }
        
        .no-orders i {
            font-size: 60px;
            margin-bottom: 20px;
            color: var(--light-gray);
        }
        
        .no-orders h3 {
            margin-bottom: 10px;
            color: var(--gray);
        }
        
        /* ==================== MODAL ==================== */
        .modal {
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
            animation: fadeIn 0.3s ease;
        }
        
        .modal.active {
            display: flex;
        }
        
        .modal-content {
            background-color: white;
            border-radius: 15px;
            max-width: 800px;
            width: 100%;
            max-height: 90vh;
            overflow-y: auto;
            position: relative;
            animation: modalSlideIn 0.3s ease;
        }
        
        @keyframes modalSlideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
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
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: var(--transition);
        }
        
        .close-modal:hover {
            background-color: var(--light-gray);
            color: var(--dark);
        }
        
        .modal-header {
            padding: 25px 30px 15px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .modal-header h2 {
            color: var(--secondary);
            font-size: 24px;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .modal-body {
            padding: 30px;
        }
        
        .order-details-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }
        
        .detail-section {
            margin-bottom: 25px;
        }
        
        .detail-section h3 {
            color: var(--secondary);
            margin-bottom: 15px;
            font-size: 18px;
            padding-bottom: 8px;
            border-bottom: 2px solid var(--light-gray);
            display: flex;
            align-items: center;
            gap: 10px;
        }
        
        .detail-section h3 i {
            color: var(--primary);
        }
        
        .detail-item {
            display: flex;
            margin-bottom: 12px;
        }
        
        .detail-label {
            font-weight: 600;
            width: 150px;
            color: var(--secondary);
            flex-shrink: 0;
        }
        
        .items-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 10px;
        }
        
        .items-table th {
            background-color: var(--light-gray);
            padding: 12px;
            text-align: left;
            color: var(--secondary);
            font-weight: 600;
        }
        
        .items-table td {
            padding: 12px;
            border-bottom: 1px solid var(--light-gray);
        }
        
        .items-table tr:last-child td {
            border-bottom: none;
        }
        
        .modal-footer {
            padding: 20px 30px;
            border-top: 1px solid var(--light-gray);
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .status-select {
            padding: 10px 15px;
            border-radius: 6px;
            border: 1px solid var(--light-gray);
            font-size: 16px;
            min-width: 200px;
            background-color: white;
            cursor: pointer;
        }
        
        .status-select:focus {
            outline: none;
            border-color: var(--primary);
        }
        
        /* ==================== BUTTONS ==================== */
        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 12px 24px;
            border-radius: 6px;
            text-decoration: none;
            font-weight: 600;
            font-size: 16px;
            border: none;
            cursor: pointer;
            transition: var(--transition);
        }
        
        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(255, 107, 53, 0.3);
        }
        
        .btn-secondary {
            background: linear-gradient(135deg, var(--secondary) 0%, #1f2135 100%);
        }
        
        /* ==================== NOTIFICATIONS ==================== */
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, var(--success) 0%, #1e7e34 100%);
            color: white;
            padding: 15px 25px;
            border-radius: 8px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
            z-index: 3000;
            animation: slideInRight 0.3s ease, slideOutRight 0.3s ease 4.7s;
            max-width: 350px;
            font-size: 14px;
            line-height: 1.4;
        }
        
        .notification.error {
            background: linear-gradient(135deg, var(--danger) 0%, #c82333 100%);
        }
        
        .notification.warning {
            background: linear-gradient(135deg, var(--warning) 0%, #e0a800 100%);
        }
        
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
        
        @keyframes slideOutRight {
            from {
                transform: translateX(0);
                opacity: 1;
            }
            to {
                transform: translateX(100%);
                opacity: 0;
            }
        }
        
        /* ==================== RESPONSIVE ==================== */
        @media (max-width: 992px) {
            .order-details-grid {
                grid-template-columns: 1fr;
            }
            
            .orders-table {
                display: block;
                overflow-x: auto;
            }
            
            .modal-footer {
                flex-direction: column;
                gap: 15px;
                align-items: stretch;
            }
            
            .status-select {
                width: 100%;
            }
        }
        
        @media (max-width: 768px) {
            .admin-controls {
                flex-direction: column;
                align-items: stretch;
            }
            
            .search-box {
                max-width: 100%;
            }
            
            .filter-controls {
                overflow-x: auto;
                padding-bottom: 5px;
                justify-content: flex-start;
            }
            
            .stats-cards {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .admin-title h1 {
                font-size: 28px;
                flex-direction: column;
                align-items: flex-start;
                gap: 5px;
            }
        }
        
        @media (max-width: 576px) {
            .stats-cards {
                grid-template-columns: 1fr;
            }
            
            .orders-table th, 
            .orders-table td {
                padding: 12px 8px;
                font-size: 14px;
            }
            
            .action-buttons {
                flex-direction: column;
            }
            
            .action-btn {
                width: 32px;
                height: 32px;
            }
            
            .login-box {
                padding: 30px 20px;
            }
            
            .modal-body {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Login Page -->
    <div id="loginPage" class="login-container">
        <div class="login-box">
            <div class="login-logo">
                <div class="logo-icon">
                    <i class="fas fa-dumpling"></i>
                </div>
                <div class="logo-text">PANGS!T <span>Admin</span></div>
            </div>
            
            <div class="login-title">
                <h2>Masuk ke Dashboard</h2>
                <p>Pantau pesanan pelanggan secara real-time</p>
            </div>
            
            <form id="loginForm" class="login-form">
                <div class="form-group">
                    <label for="username">Username</label>
                    <input type="text" id="username" placeholder="admin" required>
                </div>
                
                <div class="form-group">
                    <label for="password">Password</label>
                    <input type="password" id="password" placeholder="admin123" required>
                </div>
                
                <button type="submit" class="btn login-btn">
                    <i class="fas fa-sign-in-alt"></i> Masuk
                </button>
                
                <div id="loginError" class="login-error">
                    <i class="fas fa-exclamation-circle"></i> Username atau password salah!
                </div>
            </form>
        </div>
    </div>
    
    <!-- Admin Dashboard -->
    <div id="adminPage">
        <!-- Header -->
        <header class="admin-header">
            <div class="container">
                <div class="admin-header-content">
                    <div class="admin-logo">
                        <div class="admin-logo-icon">
                            <i class="fas fa-dumpling"></i>
                        </div>
                        <div class="admin-logo-text">PANGS!T <span>Admin</span></div>
                    </div>
                    
                    <div class="admin-user">
                        <div class="admin-avatar">A</div>
                        <div>
                            <div style="font-weight: 600;">Administrator</div>
                            <div style="font-size: 14px; opacity: 0.8;">PANGS!T Manager</div>
                        </div>
                        <button class="logout-btn" id="logoutBtn">
                            <i class="fas fa-sign-out-alt"></i> Keluar
                        </button>
                    </div>
                </div>
            </div>
        </header>
        
        <!-- Main Content -->
        <main class="admin-main">
            <div class="container">
                <!-- Title -->
                <div class="admin-title">
                    <h1>
                        <i class="fas fa-shopping-cart"></i> Manajemen Pesanan
                        <span class="live-badge"><i class="fas fa-circle"></i> LIVE</span>
                    </h1>
                    <p>Pesanan baru akan muncul otomatis dalam 3 detik</p>
                </div>
                
                <!-- Stats -->
                <div class="stats-cards">
                    <div class="stat-card" data-filter="pending">
                        <div class="stat-icon pending">
                            <i class="fas fa-clock"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="pendingCount">0</h3>
                            <p>Menunggu Konfirmasi</p>
                        </div>
                    </div>
                    
                    <div class="stat-card" data-filter="processing">
                        <div class="stat-icon processing">
                            <i class="fas fa-truck"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="processingCount">0</h3>
                            <p>Sedang Diproses</p>
                        </div>
                    </div>
                    
                    <div class="stat-card" data-filter="completed">
                        <div class="stat-icon completed">
                            <i class="fas fa-check-circle"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="completedCount">0</h3>
                            <p>Selesai</p>
                        </div>
                    </div>
                    
                    <div class="stat-card" data-filter="all">
                        <div class="stat-icon total">
                            <i class="fas fa-chart-line"></i>
                        </div>
                        <div class="stat-info">
                            <h3 id="totalOrdersCount">0</h3>
                            <p>Total Pesanan</p>
                        </div>
                    </div>
                </div>
                
                <!-- Controls -->
                <div class="admin-controls">
                    <div class="search-box">
                        <i class="fas fa-search search-icon"></i>
                        <input type="text" id="searchOrders" placeholder="Cari pesanan, nama pelanggan, atau ID...">
                    </div>
                    
                    <div class="filter-controls">
                        <button class="filter-btn active" data-status="all">
                            <i class="fas fa-list"></i> Semua
                        </button>
                        <button class="filter-btn" data-status="pending">
                            <i class="fas fa-clock"></i> Menunggu
                        </button>
                        <button class="filter-btn" data-status="processing">
                            <i class="fas fa-truck"></i> Diproses
                        </button>
                        <button class="filter-btn" data-status="completed">
                            <i class="fas fa-check-circle"></i> Selesai
                        </button>
                        <button class="filter-btn" data-status="cancelled">
                            <i class="fas fa-times-circle"></i> Dibatalkan
                        </button>
                    </div>
                </div>
                
                <!-- Orders Table -->
                <div class="orders-table-container">
                    <div class="table-header">
                        <h3><i class="fas fa-table"></i> Daftar Pesanan</h3>
                        <button class="refresh-btn" id="refreshBtn">
                            <i class="fas fa-sync-alt"></i> Refresh
                        </button>
                    </div>
                    
                    <table class="orders-table">
                        <thead>
                            <tr>
                                <th>ID Pesanan</th>
                                <th>Pelanggan</th>
                                <th>Produk</th>
                                <th>Jumlah</th>
                                <th>Total</th>
                                <th>Metode Bayar</th>
                                <th>Status</th>
                                <th>Tanggal</th>
                                <th>Aksi</th>
                            </tr>
                        </thead>
                        <tbody id="ordersTableBody">
                            <!-- Data akan dimuat otomatis -->
                        </tbody>
                    </table>
                    
                    <div id="noOrdersMessage" class="no-orders" style="display: none;">
                        <i class="fas fa-shopping-cart"></i>
                        <h3>Belum ada pesanan</h3>
                        <p>Pesanan dari pelanggan akan muncul di sini</p>
                    </div>
                </div>
            </div>
        </main>
    </div>
    
    <!-- Order Detail Modal -->
    <div class="modal" id="orderDetailModal">
        <div class="modal-content">
            <button class="close-modal" id="closeDetailModal">&times;</button>
            <div class="modal-header">
                <h2><i class="fas fa-file-invoice"></i> Detail Pesanan</h2>
            </div>
            <div class="modal-body" id="orderDetailContent">
                <!-- Content akan diisi oleh JavaScript -->
            </div>
            <div class="modal-footer">
                <select class="status-select" id="statusSelect">
                    <option value="pending">Menunggu Konfirmasi</option>
                    <option value="processing">Sedang Diproses</option>
                    <option value="completed">Selesai</option>
                    <option value="cancelled">Dibatalkan</option>
                </select>
                <div>
                    <button class="btn btn-secondary" id="closeDetailBtn">
                        <i class="fas fa-times"></i> Tutup
                    </button>
                    <button class="btn" id="updateStatusBtn">
                        <i class="fas fa-save"></i> Update Status
                    </button>
                </div>
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
            ORDERS: 'pangsit_admin_orders',
            NEW_ORDER_FLAG: 'pangsit_new_order_flag',
            LAST_CHECK: 'pangsit_admin_last_check'
        };
        
        // ==================== VARIABEL GLOBAL ====================
        let orders = [];
        let lastOrderCount = 0;
        let currentFilter = 'all';
        let currentSearch = '';
        let monitoringInterval = null;
        let currentOrderId = null;
        
        // ==================== FUNGSI UTAMA ====================
        
        // Format Rupiah
        function formatRupiah(amount) {
            return new Intl.NumberFormat('id-ID', {
                style: 'currency',
                currency: 'IDR',
                minimumFractionDigits: 0
            }).format(amount);
        }
        
        // Format Tanggal
        function formatDate(dateString) {
            if (!dateString) return '-';
            try {
                const date = new Date(dateString);
                if (isNaN(date.getTime())) {
                    return dateString; // Return as is if not valid date
                }
                return date.toLocaleDateString('id-ID', {
                    day: 'numeric',
                    month: 'short',
                    year: 'numeric',
                    hour: '2-digit',
                    minute: '2-digit'
                });
            } catch (e) {
                return dateString;
            }
        }
        
        // Load orders dari localStorage
        function loadOrders() {
            try {
                const stored = localStorage.getItem(STORAGE_KEYS.ORDERS);
                orders = stored ? JSON.parse(stored) : [];
                // Sort by timestamp (newest first)
                orders.sort((a, b) => (b.timestamp || 0) - (a.timestamp || 0));
                return orders;
            } catch (error) {
                console.error('Error loading orders:', error);
                return [];
            }
        }
        
        // Update Statistics
        function updateStats() {
            const pendingCount = orders.filter(o => o.status === 'pending').length;
            const processingCount = orders.filter(o => o.status === 'processing').length;
            const completedCount = orders.filter(o => o.status === 'completed').length;
            const totalOrdersCount = orders.length;
            
            document.getElementById('pendingCount').textContent = pendingCount;
            document.getElementById('processingCount').textContent = processingCount;
            document.getElementById('completedCount').textContent = completedCount;
            document.getElementById('totalOrdersCount').textContent = totalOrdersCount;
        }
        
        // Render Orders Table
        function renderOrdersTable(filteredOrders = orders) {
            const tbody = document.getElementById('ordersTableBody');
            const noOrdersMessage = document.getElementById('noOrdersMessage');
            
            tbody.innerHTML = '';
            
            if (filteredOrders.length === 0) {
                noOrdersMessage.style.display = 'block';
                return;
            }
            
            noOrdersMessage.style.display = 'none';
            
            filteredOrders.forEach((order, index) => {
                const row = document.createElement('tr');
                
                // Check if order is new (last 5 minutes)
                if (isNewOrder(order)) {
                    row.classList.add('new-order');
                }
                
                // Calculate total items
                const totalItems = order.products ? order.products.reduce((sum, product) => sum + (product.quantity || 1), 0) : 0;
                
                // Status badge
                let statusClass, statusText;
                switch(order.status) {
                    case 'pending':
                        statusClass = 'status-pending';
                        statusText = 'Menunggu';
                        break;
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
                    default:
                        statusClass = 'status-pending';
                        statusText = 'Menunggu';
                }
                
                row.innerHTML = `
                    <td class="order-id">${order.id || 'N/A'}</td>
                    <td>
                        <div class="customer-info">
                            <div class="customer-name">${order.customer?.name || 'Tidak ada nama'}</div>
                            <div class="customer-phone">${order.customer?.phone || 'Tidak ada telepon'}</div>
                        </div>
                    </td>
                    <td>
                        <ul class="product-list">
                            ${order.products ? order.products.map(p => 
                                `<li>${p.name || 'Produk'} x${p.quantity || 1}</li>`
                            ).join('') : '<li>Tidak ada produk</li>'}
                        </ul>
                    </td>
                    <td>${totalItems} item</td>
                    <td>${formatRupiah(order.total || 0)}</td>
                    <td>${order.paymentMethod ? order.paymentMethod.toUpperCase() : 'N/A'}</td>
                    <td>
                        <span class="status-badge ${statusClass}">${statusText}</span>
                    </td>
                    <td>${formatDate(order.date || order.timestamp)}</td>
                    <td>
                        <div class="action-buttons">
                            <button class="action-btn view" data-id="${order.id || ''}">
                                <i class="fas fa-eye"></i>
                            </button>
                            <button class="action-btn edit" data-id="${order.id || ''}">
                                <i class="fas fa-edit"></i>
                            </button>
                        </div>
                    </td>
                `;
                
                tbody.appendChild(row);
            });
            
            // Add event listeners
            attachOrderActions();
        }
        
        // Check if order is new (last 5 minutes)
        function isNewOrder(order) {
            const fiveMinutesAgo = Date.now() - (5 * 60 * 1000);
            return order.timestamp > fiveMinutesAgo;
        }
        
        // Check for new orders
        function checkForNewOrders() {
            const currentOrders = loadOrders();
            const newOrderFlag = localStorage.getItem('pangsit_new_order');
            
            // Check if there are new orders
            if (currentOrders.length > lastOrderCount || newOrderFlag) {
                const newOrdersCount = currentOrders.length - lastOrderCount;
                orders = currentOrders;
                lastOrderCount = currentOrders.length;
                
                // Apply current filter
                let filteredOrders = orders;
                if (currentFilter !== 'all') {
                    filteredOrders = orders.filter(o => o.status === currentFilter);
                }
                if (currentSearch) {
                    filteredOrders = filteredOrders.filter(o => 
                        (o.id && o.id.toLowerCase().includes(currentSearch)) ||
                        (o.customer?.name && o.customer.name.toLowerCase().includes(currentSearch))
                    );
                }
                
                renderOrdersTable(filteredOrders);
                updateStats();
                
                if (newOrdersCount > 0 && newOrderFlag) {
                    try {
                        const newOrder = JSON.parse(newOrderFlag);
                        showNotification(
                            `📦 Pesanan Baru: ${newOrder.id}<br>
                             👤 ${newOrder.customer}<br>
                             💰 ${formatRupiah(newOrder.total)}`,
                            'success'
                        );
                    } catch (e) {
                        showNotification(`${newOrdersCount} pesanan baru masuk!`, 'success');
                    }
                }
                
                // Clear the flag
                localStorage.removeItem('pangsit_new_order');
            }
            
            // Update last check time
            localStorage.setItem(STORAGE_KEYS.LAST_CHECK, Date.now().toString());
        }
        
        // Filter orders
        function filterOrders(status) {
            currentFilter = status;
            if (status === 'all') return orders;
            return orders.filter(o => o.status === status);
        }
        
        // Search orders
        function searchOrders(query) {
            currentSearch = query.toLowerCase();
            const filtered = orders.filter(o => 
                (o.id && o.id.toLowerCase().includes(currentSearch)) ||
                (o.customer?.name && o.customer.name.toLowerCase().includes(currentSearch)) ||
                (o.customer?.phone && o.customer.phone.includes(query)) ||
                (o.products && o.products.some(p => p.name && p.name.toLowerCase().includes(currentSearch)))
            );
            return filtered;
        }
        
        // Show order detail
        function showOrderDetail(orderId) {
            const order = orders.find(o => o.id === orderId);
            if (!order) {
                showNotification('Pesanan tidak ditemukan', 'error');
                return;
            }
            
            // Format payment method
            let paymentMethodText = order.paymentMethod || 'N/A';
            switch(paymentMethodText.toLowerCase()) {
                case 'gopay': paymentMethodText = 'GoPay'; break;
                case 'ovo': paymentMethodText = 'OVO'; break;
                case 'dana': paymentMethodText = 'DANA'; break;
                case 'transfer': paymentMethodText = 'Transfer Bank'; break;
            }
            
            // Format status
            let statusText = 'Menunggu Konfirmasi';
            switch(order.status) {
                case 'processing': statusText = 'Sedang Diproses'; break;
                case 'completed': statusText = 'Selesai'; break;
                case 'cancelled': statusText = 'Dibatalkan'; break;
            }
            
            const content = document.getElementById('orderDetailContent');
            content.innerHTML = `
                <div class="order-details-grid">
                    <div>
                        <div class="detail-section">
                            <h3><i class="fas fa-info-circle"></i> Informasi Pesanan</h3>
                            <div class="detail-item">
                                <span class="detail-label">ID Pesanan:</span>
                                <span>${order.id || 'N/A'}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Tanggal:</span>
                                <span>${formatDate(order.date || order.timestamp)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Status:</span>
                                <span><strong>${statusText}</strong></span>
                            </div>
                        </div>
                        
                        <div class="detail-section">
                            <h3><i class="fas fa-user"></i> Informasi Pelanggan</h3>
                            <div class="detail-item">
                                <span class="detail-label">Nama:</span>
                                <span>${order.customer?.name || 'Tidak ada nama'}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Telepon:</span>
                                <span>${order.customer?.phone || 'Tidak ada telepon'}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Alamat:</span>
                                <span>${order.customer?.address || 'Tidak ada alamat'}</span>
                            </div>
                        </div>
                    </div>
                    
                    <div>
                        <div class="detail-section">
                            <h3><i class="fas fa-credit-card"></i> Informasi Pembayaran</h3>
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
                            <h3><i class="fas fa-sticky-note"></i> Catatan</h3>
                            <p>${order.notes}</p>
                        </div>
                        ` : ''}
                    </div>
                </div>
                
                <div class="detail-section">
                    <h3><i class="fas fa-box"></i> Detail Produk</h3>
                    <table class="items-table">
                        <thead>
                            <tr>
                                <th>Produk</th>
                                <th>Harga</th>
                                <th>Jumlah</th>
                                <th>Subtotal</th>
                            </tr>
                        </thead>
                        <tbody>
                            ${order.products ? order.products.map(p => `
                                <tr>
                                    <td>${p.name || 'Produk'}</td>
                                    <td>${formatRupiah(p.price || 0)}</td>
                                    <td>${p.quantity || 1}</td>
                                    <td>${formatRupiah((p.price || 0) * (p.quantity || 1))}</td>
                                </tr>
                            `).join('') : `
                                <tr>
                                    <td colspan="4" style="text-align: center;">Tidak ada produk</td>
                                </tr>
                            `}
                        </tbody>
                    </table>
                </div>
            `;
            
            // Set current status in select
            document.getElementById('statusSelect').value = order.status || 'pending';
            
            // Save order ID for update
            document.getElementById('orderDetailModal').dataset.orderId = orderId;
            
            // Show modal
            document.getElementById('orderDetailModal').classList.add('active');
        }
        
        // Update order status
        function updateOrderStatus(orderId, newStatus) {
            const order = orders.find(o => o.id === orderId);
            if (order) {
                order.status = newStatus;
                
                // Save to localStorage
                localStorage.setItem(STORAGE_KEYS.ORDERS, JSON.stringify(orders));
                
                // Re-render table
                let filteredOrders = orders;
                if (currentFilter !== 'all') {
                    filteredOrders = orders.filter(o => o.status === currentFilter);
                }
                if (currentSearch) {
                    filteredOrders = filteredOrders.filter(o => 
                        (o.id && o.id.toLowerCase().includes(currentSearch)) ||
                        (o.customer?.name && o.customer.name.toLowerCase().includes(currentSearch))
                    );
                }
                
                renderOrdersTable(filteredOrders);
                updateStats();
                
                showNotification(`Status pesanan ${orderId} diubah ke ${newStatus}`, 'success');
                return true;
            }
            return false;
        }
        
        // Attach event listeners to order actions
        function attachOrderActions() {
            // View buttons
            document.querySelectorAll('.action-btn.view').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    if (orderId) {
                        showOrderDetail(orderId);
                    }
                });
            });
            
            // Edit buttons
            document.querySelectorAll('.action-btn.edit').forEach(btn => {
                btn.addEventListener('click', function() {
                    const orderId = this.getAttribute('data-id');
                    if (orderId) {
                        showOrderDetail(orderId);
                    }
                });
            });
        }
        
        // Show notification
        function showNotification(message, type = 'success') {
            // Remove existing notification
            const existingNotification = document.querySelector('.notification');
            if (existingNotification) {
                existingNotification.remove();
            }
            
            // Create notification element
            const notification = document.createElement('div');
            notification.className = `notification ${type}`;
            notification.innerHTML = message;
            
            document.body.appendChild(notification);
            
            // Auto remove after 5 seconds
            setTimeout(() => {
                if (notification.parentNode) {
                    notification.parentNode.removeChild(notification);
                }
            }, 5000);
        }
        
        // Start real-time monitoring
        function startMonitoring() {
            // Initial load
            loadOrders();
            lastOrderCount = orders.length;
            renderOrdersTable();
            updateStats();
            
            // Start interval for checking new orders (every 3 seconds)
            monitoringInterval = setInterval(checkForNewOrders, 3000);
            
            // Listen for storage events (from other tabs)
            window.addEventListener('storage', function(e) {
                if (e.key === STORAGE_KEYS.ORDERS || e.key === 'pangsit_new_order') {
                    checkForNewOrders();
                }
            });
            
            // Listen for custom events
            window.addEventListener('newPangsitOrder', function(e) {
                if (e.detail) {
                    orders.unshift(e.detail);
                    lastOrderCount = orders.length;
                    
                    // Apply current filter
                    let filteredOrders = orders;
                    if (currentFilter !== 'all') {
                        filteredOrders = orders.filter(o => o.status === currentFilter);
                    }
                    
                    renderOrdersTable(filteredOrders);
                    updateStats();
                    
                    showNotification(
                        `🔥 PESANAN BARU LANGSUNG!<br>
                         📋 ${e.detail.id}<br>
                         👤 ${e.detail.customer?.name || 'Pelanggan'}<br>
                         💰 ${formatRupiah(e.detail.total || 0)}`,
                        'success'
                    );
                }
            });
            
            // Also check when window gets focus
            window.addEventListener('focus', checkForNewOrders);
            
            console.log('🔔 Monitoring pesanan diaktifkan');
        }
        
        // Stop monitoring
        function stopMonitoring() {
            if (monitoringInterval) {
                clearInterval(monitoringInterval);
                monitoringInterval = null;
            }
        }
        
        // Initialize admin dashboard
        function initAdmin() {
            startMonitoring();
            
            // Filter buttons
            document.querySelectorAll('.filter-btn').forEach(btn => {
                btn.addEventListener('click', function() {
                    document.querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
                    this.classList.add('active');
                    
                    currentFilter = this.getAttribute('data-status');
                    const filtered = filterOrders(currentFilter);
                    renderOrdersTable(filtered);
                });
            });
            
            // Search input
            document.getElementById('searchOrders').addEventListener('input', function() {
                const query = this.value;
                if (query.trim() === '') {
                    const filtered = filterOrders(currentFilter);
                    renderOrdersTable(filtered);
                } else {
                    const filtered = searchOrders(query);
                    renderOrdersTable(filtered);
                }
            });
            
            // Refresh button
            document.getElementById('refreshBtn').addEventListener('click', function() {
                this.classList.add('rotating');
                checkForNewOrders();
                setTimeout(() => {
                    this.classList.remove('rotating');
                }, 1000);
            });
            
            // Modal close buttons
            document.getElementById('closeDetailModal').addEventListener('click', () => {
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
                const orderId = document.getElementById('orderDetailModal').dataset.orderId;
                const newStatus = document.getElementById('statusSelect').value;
                
                if (orderId && updateOrderStatus(orderId, newStatus)) {
                    document.getElementById('orderDetailModal').classList.remove('active');
                }
            });
            
            // Logout button
            document.getElementById('logoutBtn').addEventListener('click', () => {
                stopMonitoring();
                localStorage.removeItem('pangsit_admin_logged_in');
                document.getElementById('adminPage').style.display = 'none';
                document.getElementById('loginPage').style.display = 'flex';
            });
            
            // Add event listener to stat cards for filtering
            document.querySelectorAll('.stat-card[data-filter]').forEach(card => {
                card.addEventListener('click', function() {
                    const filter = this.getAttribute('data-filter');
                    const filterBtn = document.querySelector(`.filter-btn[data-status="${filter}"]`);
                    if (filterBtn) {
                        filterBtn.click();
                    }
                });
            });
        }
        
        // Login function
        function initLogin() {
            document.getElementById('loginForm').addEventListener('submit', function(e) {
                e.preventDefault();
                
                const username = document.getElementById('username').value;
                const password = document.getElementById('password').value;
                const errorElement = document.getElementById('loginError');
                
                if (username === ADMIN_CREDENTIALS.username && password === ADMIN_CREDENTIALS.password) {
                    errorElement.style.display = 'none';
                    localStorage.setItem('pangsit_admin_logged_in', 'true');
                    
                    document.getElementById('loginPage').style.display = 'none';
                    document.getElementById('adminPage').style.display = 'block';
                    
                    initAdmin();
                } else {
                    errorElement.style.display = 'block';
                }
            });
        }
        
        // Initialize on page load
        document.addEventListener('DOMContentLoaded', () => {
            // Add CSS animations for notifications
            const style = document.createElement('style');
            style.textContent = `
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
                
                @keyframes slideOutRight {
                    from {
                        transform: translateX(0);
                        opacity: 1;
                    }
                    to {
                        transform: translateX(100%);
                        opacity: 0;
                    }
                }
                
                @keyframes pulse {
                    0% { transform: scale(1); }
                    50% { transform: scale(1.05); }
                    100% { transform: scale(1); }
                }
            `;
            document.head.appendChild(style);
            
            // Check if already logged in
            const isLoggedIn = localStorage.getItem('pangsit_admin_logged_in') === 'true';
            
            if (isLoggedIn) {
                document.getElementById('loginPage').style.display = 'none';
                document.getElementById('adminPage').style.display = 'block';
                initAdmin();
            } else {
                document.getElementById('loginPage').style.display = 'flex';
                document.getElementById('adminPage').style.display = 'none';
                initLogin();
            }
            
            // Auto-fill login for testing (remove in production)
            document.getElementById('username').value = 'admin';
            document.getElementById('password').value = 'admin123';
        });
    </script>
</body>
</html>
