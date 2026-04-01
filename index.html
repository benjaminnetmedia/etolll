<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>E-Toll Master Pro</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf-autotable/3.5.23/jspdf.plugin.autotable.min.js"></script>
    <style>
        :root { --primary: #1a237e; --secondary: #0d47a1; --accent: #ffc107; --danger: #d32f2f; }
        body { font-family: 'Roboto', sans-serif; margin: 0; background: #f0f2f5; color: #333; overflow-x: hidden; }
        .header { background: var(--primary); color: white; padding: 15px; text-align: center; position: sticky; top: 0; z-index: 100; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
        .card-canvas { margin: 15px; padding: 20px; border-radius: 15px; background: linear-gradient(45deg, #1a237e, #00c853); color: white; position: relative; min-height: 160px; box-shadow: 0 10px 20px rgba(0,0,0,0.15); }
        .status-badge { position: absolute; top: 10px; right: 10px; font-size: 10px; background: rgba(255,255,255,0.2); padding: 3px 8px; border-radius: 10px; }
        .balance-label { font-size: 12px; opacity: 0.8; }
        .balance-value { font-size: 28px; font-weight: bold; margin-bottom: 10px; }
        .card-number { font-family: 'Courier New', monospace; font-size: 18px; letter-spacing: 2px; }
        
        .main-menu { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; padding: 15px; }
        .menu-btn { background: white; padding: 15px 5px; border-radius: 12px; text-align: center; box-shadow: 0 2px 4px rgba(0,0,0,0.05); font-size: 11px; font-weight: bold; cursor: pointer; border: none; }
        .menu-btn i { display: block; font-size: 24px; margin-bottom: 5px; }

        .modal { display: none; position: fixed; inset: 0; background: rgba(0,0,0,0.6); z-index: 1000; padding: 20px; overflow-y: auto; }
        .modal-content { background: white; border-radius: 15px; padding: 20px; max-width: 500px; margin: auto; }
        input, select { width: 100%; padding: 12px; margin: 8px 0; border: 1px solid #ddd; border-radius: 8px; }
        .btn-action { background: var(--secondary); color: white; border: none; padding: 12px; width: 100%; border-radius: 8px; font-weight: bold; margin-top: 10px; }
        
        .settled-box { background: #e8f5e9; padding: 15px; margin: 15px; border-radius: 10px; border-left: 5px solid #2e7d32; }
        .history-table { width: 100%; font-size: 11px; border-collapse: collapse; margin-top: 10px; }
        .history-table th, .history-table td { border-bottom: 1px solid #eee; padding: 8px; text-align: left; }
    </style>
</head>
<body>

<div class="header">
    <strong>E-TOLL NFC MASTER v2.0</strong>
    <div id="live-clock" style="font-size: 12px; margin-top: 5px;"></div>
</div>

<div class="card-canvas" id="card-display">
    <div class="status-badge" id="card-issuer">MENUNGGU KARTU...</div>
    <div class="balance-label">Saldo Kartu</div>
    <div class="balance-value" id="view-balance">Rp 0</div>
    <div class="card-number" id="view-card-number">**** **** **** ****</div>
    <div style="margin-top: 15px; font-size: 11px;" id="view-card-owner">Belum Terdaftar</div>
</div>

<div class="settled-box">
    <div class="balance-label" style="color: #2e7d32">Saldo Mengendap (Revenue)</div>
    <div class="balance-value" id="view-settled" style="color: #2e7d32; font-size: 22px;">Rp 0</div>
    <button onclick="openModal('modal-wd')" style="font-size: 10px; padding: 5px; width: auto; margin: 0;">Tarik Tunai</button>
</div>

<div class="main-menu">
    <button class="menu-btn" onclick="startNFCScan()">📡<br>TAP NFC</button>
    <button class="menu-btn" onclick="openModal('modal-topup')">💰<br>TOP UP</button>
    <button class="menu-btn" onclick="openModal('modal-gate')">🛣️<br>SIMULATOR</button>
    <button class="menu-btn" onclick="openModal('modal-db')">⚙️<br>DATABASE</button>
    <button class="menu-btn" onclick="exportHistory()">📄<br>EKSPOR</button>
    <button class="menu-btn" onclick="openModal('modal-reg')">📝<br>DAFTAR</button>
</div>

<!-- Modal Simulator Gerbang -->
<div id="modal-gate" class="modal">
    <div class="modal-content">
        <h3>Gate Tol Simulator</h3>
        <label>Pilih Gerbang Asal:</label>
        <select id="sel-asal" onchange="calcTarif()"></select>
        <label>Pilih Gerbang Keluar:</label>
        <select id="sel-tujuan" onchange="calcTarif()"></select>
        <label>Golongan Kendaraan:</label>
        <select id="sel-gol" onchange="calcTarif()">
            <option value="gol1">Golongan I (Sedan, Bus)</option>
            <option value="gol2">Golongan II (Truk 2 Gandar)</option>
            <option value="gol3">Golongan III (Truk 3 Gandar)</option>
            <option value="gol4">Golongan IV (Truk 4 Gandar)</option>
        </select>
        <label>Custom Waktu (Opsional):</label>
        <input type="datetime-local" id="custom-time">
        <h2 id="display-tarif" style="text-align: center; color: var(--danger);">Rp 0</h2>
        <button class="btn-action" onclick="prosesBayarTol()">BAYAR SEKARANG</button>
        <button class="btn-action" style="background:#666" onclick="closeModal()">TUTUP</button>
    </div>
</div>

<!-- Modal TopUp -->
<div id="modal-topup" class="modal">
    <div class="modal-content">
        <h3>Top Up Saldo</h3>
        <input type="number" id="topup-amount" placeholder="Nominal Rp">
        <select id="topup-method">
            <option>QRIS ALL PAYMENT</option>
            <option>M-Banking BCA</option>
            <option>M-Banking MANDIRI</option>
            <option>DANA / OVO</option>
        </select>
        <button class="btn-action" onclick="prosesTopUp()">KONFIRMASI TOP UP</button>
        <button class="btn-action" style="background:#666" onclick="closeModal()">TUTUP</button>
    </div>
</div>

<div id="history-section" style="padding: 15px;">
    <h4>Log Transaksi</h4>
    <div style="overflow-x: auto;">
        <table class="history-table" id="table-log">
            <thead>
                <tr><th>Waktu</th><th>Ket</th><th>Nominal</th></tr>
            </thead>
            <tbody id="log-body"></tbody>
        </table>
    </div>
</div>

<script src="app.js"></script>
</body>
</html>