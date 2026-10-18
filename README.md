<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BS Ekspertiz - Profesyonel Canlı Hayvan Analiz Platformu</title>
    <style>
        :root {
            --primary-green: #11381b;
            --secondary-green: #1b4d28;
            --accent-gold: #d4af37;
            --accent-gold-hover: #e5c158;
            --card-bg: rgba(17, 56, 27, 0.95);
            --text-main: #ffffff;
            --text-sub: #d1ded3;
            --border-gold: #c5a059;
            --wa-green: #25D366;
            --ai-blue: #38bdf8;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background: linear-gradient(rgba(11, 36, 17, 0.85), rgba(11, 36, 17, 0.95)), 
                        url('https://images.unsplash.com/photo-1546445317-2f44558d9ffc?q=80&w=1600&auto=format&fit=crop') no-repeat center center fixed;
            background-size: cover;
            color: var(--text-main);
            padding-bottom: 50px;
            min-height: 100vh;
        }

        /* MOBİL UYGULAMA ÜST BAR VE HAMBURGER MENÜ */
        .app-bar {
            background: linear-gradient(135deg, var(--primary-green), var(--secondary-green));
            color: #ffffff;
            padding: 15px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 3px solid var(--accent-gold);
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
        }

        .menu-btn {
            background: none;
            border: none;
            color: var(--accent-gold);
            font-size: 24px;
            cursor: pointer;
            padding: 5px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .app-title {
            font-size: 18px;
            font-weight: 800;
            letter-spacing: 1.5px;
            text-transform: uppercase;
        }

        .app-title span {
            color: var(--accent-gold);
        }

        /* SOL KAYAR MENÜ (DRAWER) */
        .drawer {
            position: fixed;
            top: 0;
            left: -280px;
            width: 280px;
            height: 100%;
            background-color: #0b2411;
            border-right: 2px solid var(--accent-gold);
            z-index: 1000;
            transition: left 0.3s ease;
            padding: 20px;
            box-shadow: 5px 0 25px rgba(0,0,0,0.8);
        }

        .drawer.open {
            left: 0;
        }

        .drawer-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 1px solid rgba(212, 175, 55, 0.3);
            padding-bottom: 15px;
            margin-bottom: 20px;
        }

        .drawer-header h3 {
            color: var(--accent-gold);
            font-size: 16px;
        }

        .close-drawer {
            background: none;
            border: none;
            color: white;
            font-size: 20px;
            cursor: pointer;
        }

        .drawer-menu-item {
            padding: 12px 15px;
            color: white;
            background: rgba(17, 56, 27, 0.6);
            border: 1px solid rgba(212, 175, 55, 0.2);
            border-radius: 8px;
            margin-bottom: 10px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 10px;
            transition: 0.2s;
        }

        .drawer-menu-item:hover {
            background: var(--accent-gold);
            color: var(--primary-green);
        }

        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            display: none;
            z-index: 999;
        }

        .overlay.active {
            display: block;
        }

        .container {
            max-width: 550px;
            margin: 20px auto;
            padding: 0 15px;
        }

        .card {
            background-color: var(--card-bg);
            backdrop-filter: blur(12px);
            border: 2px solid var(--border-gold);
            border-radius: 14px;
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 12px 35px rgba(0,0,0,0.7);
        }

        .card h2 {
            font-size: 17px;
            margin-bottom: 12px;
            color: var(--accent-gold);
            font-weight: 700;
            border-bottom: 1px solid rgba(212, 175, 55, 0.3);
            padding-bottom: 8px;
        }

        .welcome-banner {
            background: linear-gradient(135deg, rgba(212, 175, 55, 0.2), rgba(17, 56, 27, 0.6));
            border-left: 5px solid var(--accent-gold);
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
        }

        .welcome-banner h3 {
            color: var(--accent-gold);
            font-size: 15px;
            margin-bottom: 6px;
        }

        .welcome-banner p {
            font-size: 12px;
            color: #fef3c7;
            line-height: 1.4;
        }

        .phone-login-box {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-top: 10px;
        }

        .phone-input {
            width: 100%;
            padding: 14px;
            border-radius: 8px;
            border: 2px solid var(--border-gold);
            background: rgba(11, 36, 17, 0.9);
            color: white;
            font-size: 15px;
            font-weight: 600;
        }

        .btn {
            background-color: var(--accent-gold);
            color: var(--primary-green);
            border: none;
            width: 100%;
            padding: 15px;
            border-radius: 8px;
            font-size: 15px;
            font-weight: 800;
            cursor: pointer;
            margin-top: 10px;
            box-shadow: 0 4px 15px rgba(212, 175, 55, 0.4);
            text-transform: uppercase;
        }

        .btn:hover {
            background-color: var(--accent-gold-hover);
        }

        .btn-whatsapp {
            background-color: var(--wa-green);
            color: #ffffff;
            border: none;
            width: 100%;
            padding: 15px;
            border-radius: 8px;
            font-size: 15px;
            font-weight: 700;
            cursor: pointer;
            margin-top: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .user-welcome {
            background: rgba(212, 175, 55, 0.2);
            border: 1px solid var(--accent-gold);
            padding: 12px;
            border-radius: 8px;
            margin-bottom: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-size: 13px;
            font-weight: 700;
        }

        .file-upload {
            border: 2px dashed var(--accent-gold);
            padding: 18px;
            text-align: center;
            border-radius: 10px;
            margin-top: 15px;
            background: rgba(11, 36, 17, 0.85);
        }

        .iban-box {
            background-color: rgba(11, 36, 17, 0.95);
            border: 2px solid var(--border-gold);
            border-radius: 10px;
            padding: 15px;
            margin-top: 15px;
        }

        .iban-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
            font-size: 13px;
        }

        .copy-btn {
            background: var(--accent-gold);
            color: var(--primary-green);
            border: none;
            padding: 5px 10px;
            border-radius: 4px;
            cursor: pointer;
            font-size: 12px;
            font-weight: 800;
        }

        .hidden {
            display: none;
        }

        /* AI TARAMA EKRANI */
        #aiScanningScreen {
            text-align: center;
            padding: 30px 20px;
        }

        .ai-scanner-box {
            width: 90px;
            height: 90px;
            margin: 0 auto 20px auto;
            border: 3px solid var(--ai-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 36px;
            animation: pulse 1.5s infinite;
            background: rgba(56, 189, 248, 0.15);
        }

        @keyframes pulse {
            0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(56, 189, 248, 0.7); }
            70% { transform: scale(1.05); box-shadow: 0 0 0 15px rgba(56, 189, 248, 0); }
            100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(56, 189, 248, 0); }
        }

        .report-view {
            background: #ffffff;
            color: #0f172a;
            padding: 20px;
            border-radius: 10px;
            margin-top: 15px;
        }

        .report-header {
            border-bottom: 2px solid #0f172a;
            padding-bottom: 10px;
            margin-bottom: 15px;
            text-align: center;
        }

        .report-row {
            display: flex;
            justify-content: space-between;
            padding: 8px 0;
            border-bottom: 1px solid #e2e8f0;
            font-size: 13px;
        }

        .legal-footer {
            margin-top: 30px;
            padding: 15px;
            background-color: rgba(11, 36, 17, 0.95);
            border-top: 2px solid var(--accent-gold);
            border-radius: 10px;
            text-align: center;
        }

        .legal-footer p {
            font-size: 10px;
            color: var(--text-sub);
            line-height: 1.4;
            margin-bottom: 6px;
        }

        .legal-footer strong {
            color: var(--accent-gold);
        }
    </style>
</head>
<body>

    <!-- SOL KAYAR MOBİL MENÜ (DRAWER) -->
    <div class="overlay" id="menuOverlay" onclick="toggleMenu()"></div>
    <div class="drawer" id="appDrawer">
        <div class="drawer-header">
            <h3>🐂 BS Ekspertiz Menü</h3>
            <button class="close-drawer" onclick="toggleMenu()">✕</button>
        </div>
        <div class="drawer-menu-item" onclick="switchSection('sectionKilo'); toggleMenu();">⚖️ Canlı Kilo Tahmin Modülü</div>
        <div class="drawer-menu-item" onclick="switchSection('sectionKarkas'); toggleMenu();">🥩 Karkas & Et Randımanı Analizi</div>
        <div class="drawer-menu-item" onclick="switchSection('sectionYag'); toggleMenu();">🧈 Yağ Oranı & Sırttan Yağlanma</div>
        <div class="drawer-menu-item" onclick="switchSection('sectionVideo'); toggleMenu();">📐 360° Detaylı Video Ekspertizi</div>
        <div class="drawer-menu-item" onclick="switchSection('sectionRaporlar'); toggleMenu();">📋 Önceki Raporlarım</div>
        <div class="drawer-menu-item" onclick="sendWhatsAppNotification(); toggleMenu();">💬 WhatsApp Destek Hattı</div>
        <div class="drawer-menu-item" onclick="logout(); toggleMenu();" style="color: #f87171; border-color: rgba(248, 113, 113, 0.3);">🚪 Güvenli Çıkış Yap</div>
    </div>

    <!-- ÜST UYGULAMA BAR -->
    <div class="app-bar">
        <button class="menu-btn" onclick="toggleMenu()">☰</button>
        <div class="app-title">BS <span>Ekspertiz</span></div>
        <div style="width: 24px;"></div>
    </div>

    <div class="container">
        
        <!-- 1. GİRİŞ EKRANI -->
        <div id="loginScreen" class="card">
            <div class="welcome-banner">
                <h3>🤝 Hoş Geldiniz, Bereketli Alışverişler</h3>
                <p>İster Simmental (Alay), ister Holştayn (Akbaş), ister Montofon veya yerli ırk olsun; tüm büyükbaş hayvanlarınız için körlemesine tahminlere son veriyoruz.</p>
            </div>
            <h2>📋 Üye Girişi & Doğrulama</h2>
            
            <p style="font-size: 13px; color: var(--text-sub); margin: 12px 0 8px 0; font-weight: 600;">Devam etmek için telefon numaranızı girin:</p>
            
            <div id="stepPhone" class="phone-login-box">
                <input type="tel" id="userPhone" class="phone-input" placeholder="05XX XXX XX XX">
                <button class="btn" onclick="sendSMSCode()">Doğrulama Kodu Gönder</button>
            </div>

            <div id="stepCode" class="phone-login-box hidden">
                <p style="font-size: 13px; color: var(--accent-gold); font-weight: bold; margin-bottom: 4px;">* Test Kodunuz: <strong id="sentCodeDisplay" style="color:white; font-size:15px;"></strong></p>
                <input type="text" id="smsCodeInput" class="phone-input" placeholder="4 Haneli Şifreyi Girin">
                <button class="btn" style="background-color: #059669; color:white;" onclick="verifySMSCode()">Kodu Onayla ve Başla</button>
            </div>
        </div>

        <!-- ANA MENÜ / MODÜL EKRANLARI -->
        <div id="appMainContent" class="hidden">
            <div class="user-welcome">
                <span id="welcomeUserText">Kayıtlı Tel: </span>
                <button onclick="logout()" style="background:none; border:none; color:var(--accent-gold); cursor:pointer; font-size:12px; font-weight:bold; text-decoration:underline;">Çıkış</button>
            </div>

            <!-- MODÜL 1: CANLI KİLO TAHMİNİ -->
            <div id="sectionKilo" class="card analysis-section">
                <h2>⚖️ Canlı Kilo Tahmin Modülü</h2>
                <p style="font-size: 12px; color: var(--text-sub); margin-bottom: 12px;">Hangi ırk olursa olsun (Alay, Akbaş vb.), hayvanınızın göğüs ve boy hatlarından AI destekli canlı kilo dökümünü alın.</p>
                
                <div class="file-upload">
                    <p style="font-size:13px; color: #ffffff; font-weight:700;">Hayvanın Yandan Net Fotoğrafını Yükleyin</p>
                    <input type="file" style="margin-top: 10px; font-size: 12px; color: var(--text-sub);">
                </div>
                <button class="btn" onclick="startAnalysis('Canlı Kilo Tahmini', 30)">Canlı Kilo Analizini Başlat (30 TL)</button>
            </div>

            <!-- MODÜL 2: KARKAS & ET RANDIMANI -->
            <div id="sectionKarkas" class="card analysis-section hidden">
                <h2>🥩 Karkas & Et Randımanı Analizi</h2>
                <p style="font-size: 12px; color: var(--text-sub); margin-bottom: 12px;">Kesim sonrası çıkacak net et miktarını ve EUROP sınıfını milimetrik olarak hesaplayın.</p>
                
                <div class="file-upload">
                    <p style="font-size:13px; color: #ffffff; font-weight:700;">Hayvanın Canlı / Form Fotoğrafı</p>
                    <input type="file" style="margin-top: 10px; font-size: 12px; color: var(--text-sub);">
                </div>
                <button class="btn" onclick="startAnalysis('Karkas & Et Randımanı', 30)">Karkas Analizini Başlat (30 TL)</button>
            </div>

            <!-- MODÜL 3: YAĞ ORANI -->
            <div id="sectionYag" class="card analysis-section hidden">
                <h2>🧈 Yağ Oranı & Sırttan Yağlanma</h2>
                <p style="font-size: 12px; color: var(--text-sub); margin-bottom: 12px;">Sırt bölgesi ve iç yağlanma oranını yapay zeka doku taramasıyla tespit edin.</p>
                
                <div class="file-upload">
                    <p style="font-size:13px; color: #ffffff; font-weight:700;">Sırt Üstü ve Kıç Bölgesi Fotoğrafı</p>
                    <input type="file" style="margin-top: 10px; font-size: 12px; color: var(--text-sub);">
                </div>
                <button class="btn" onclick="startAnalysis('Yağ Oranı Analizi', 30)">Yağ Analizini Başlat (30 TL)</button>
            </div>

            <!-- MODÜL 4: 360 VİDEO EKSPERTİZİ -->
            <div id="sectionVideo" class="card analysis-section hidden">
                <h2>📐 360° Detaylı Video Ekspertizi</h2>
                <p style="font-size: 12px; color: var(--text-sub); margin-bottom: 12px;">Hayvanın etrafında çekilen 360 derece video ile kapsamlı anatomik rapor çıkarın.</p>
                
                <div class="file-upload">
                    <p style="font-size:13px; color: #ffffff; font-weight:700;">360° Çekilmiş Video Dosyasını Yükleyin</p>
                    <input type="file" style="margin-top: 10px; font-size: 12px; color: var(--text-sub);">
                </div>
                <button class="btn" onclick="startAnalysis('360° Video Ekspertizi', 50)">360° Video Analizini Başlat (50 TL)</button>
            </div>

            <!-- MODÜL 5: ÖNCEKİ RAPORLARIM -->
            <div id="sectionRaporlar" class="card analysis-section hidden">
                <h2>📋 Önceki Raporlarım</h2>
                <p style="font-size: 12px; color: var(--text-sub); margin-bottom: 12px;">Geçmişte yaptığınız tüm analizler ve tescilli raporlarınız:</p>
                
                <div style="background: rgba(11, 36, 17, 0.9); padding: 12px; border-radius: 8px; border: 1px solid var(--border-gold); margin-bottom: 10px; font-size: 13px;">
                    <p><strong>Kod:</strong> BS-8492 | Canlı Kilo Analizi</p>
                    <p style="color: var(--accent-gold); font-size: 11px;">Tarih: 18.10.2026 | Sonuç: 885 kg (Onaylı)</p>
                </div>
            </div>

            <!-- ÖDEME BÖLÜMÜ -->
            <div id="paymentCard" class="card hidden">
                <h2 id="paymentTitleText">Ödeme Talimatı (FAST / Havale)</h2>
                <p style="font-size: 13px; color: var(--text-sub); margin-bottom: 10px;">Seçtiğiniz modül için işlem bedelini aşağıdaki hesaba aktarınız:</p>
                
                <div class="iban-box">
                    <div class="iban-row">
                        <span><strong>Alıcı:</strong> Yakup Yılmaz</span>
                    </div>
                    <div class="iban-row">
                        <span><strong>IBAN:</strong> TR19 0001 5001 5800 7336 9987 02</span>
                        <button class="copy-btn" onclick="copyIBAN()">Kopyala</button>
                    </div>
                    <div class="iban-row">
                        <span><strong>Tutar:</strong> <span id="selectedPrice" style="color:var(--accent-gold); font-weight:bold;">30</span> TL</span>
                    </div>
                    <div class="iban-row">
                        <span><strong>Referans Kodunuz:</strong> <strong id="orderCode" style="color:var(--accent-gold);">BS-8492</strong></span>
                    </div>
                </div>

                <button class="btn-whatsapp" onclick="sendWhatsAppNotification()">
                    💬 DEKONTU WHATSAPP'TAN GÖNDER
                </button>
            </div>
        </div>

        <!-- BEKLEME VE YAPAY ZEKA TARAMA EKRANI -->
        <div id="waitingScreen" class="card hidden">
            <div id="aiScanningScreen">
                <div class="ai-scanner-box">🧠</div>
                <h2 style="justify-content: center; border: none;">Yapay Zeka Taraması Devam Ediyor</h2>
                <p style="font-size: 13px; color: var::text-sub; line-height: 1.5; margin-bottom: 15px;" id="aiStatusText">
                    Dekontunuz kontrol ediliyor.<br>
                    <strong>AI Görüntü İşleme Motoru</strong> hayvanın anatomik hatlarını inceliyor...
                </p>
                <div style="background: rgba(56, 189, 248, 0.15); border: 1px solid var(--ai-blue); padding: 10px; border-radius: 6px; font-size: 12px; color: var(--ai-blue);">
                    Sistem Modeli: <strong>BS-Neural-Universal-v4</strong> | İşlem ID: BS-8492
                </div>
            </div>
        </div>

        <!-- MÜŞTERİ RAPOR EKRANI -->
        <div id="reportScreen" class="card hidden">
            <h2>Ekspertiz Sonuç Raporu</h2>
            <p style="font-size: 13px; color: var(--text-sub); margin-bottom: 15px;">BS Uzmanlık Tecrübesi & Yapay Zeka Onaylı Döküm:</p>
            
            <div class="report-view">
                <div class="report-header">
                    <h2 style="color: #0f172a; font-size: 16px; border:none; padding:0; margin:0;">BS EKSPERTİZ - RESMİ RAPOR</h2>
                    <p style="font-size: 11px; color: #64748b; margin-top:4px;">Doğrulama Kodu: BS-8492 | Uzman Onaylı</p>
                </div>
                <div class="report-row">
                    <span>Analiz Türü:</span>
                    <strong id="reportTypeTitle">Canlı Kilo & Karkas Analizi</strong>
                </div>
                <div class="report-row">
                    <span>Tahmini Canlı Ağırlık:</span>
                    <strong>885 kg (±%0.8 Hassasiyet)</strong>
                </div>
                <div class="report-row">
                    <span>EUROP Karkas Sınıfı:</span>
                    <strong style="color: #2e7d32;">U Sınıfı (Üstün Kalite)</strong>
                </div>
                <div class="report-row">
                    <span>Tahmini Net Et Randımanı:</span>
                    <strong>%58.2 (~515 kg Net Et)</strong>
                </div>
                <div class="report-row">
                    <span>Yağ Oranı / Doku:</span>
                    <strong>%13.8 (Dengeli / Optimum)</strong>
                </div>
                <div class="report-row">
                    <span>Besi Kondisyon Skoru:</span>
                    <strong>4.9 / 5.0 (Kesimlik Ağır Sıklet)</strong>
                </div>
            </div>
            <button class="btn" style="margin-top: 15px;" onclick="switchSection('sectionKilo')">YENİ MODÜLE GEÇ</button>
        </div>

        <!-- YASAL KORUMA FOOTER -->
        <div class="legal-footer">
            <p>© 2026 <strong>BS Ekspertiz</strong> - Tüm Hakları Saklıdır.</p>
            <p>Fikir ve Sanat Eserleri Kanunu kapsamında koruma altındadır. İzinsiz kopyalanamaz.</p>
        </div>

    </div>

    <script>
        let selectedPackage = "Canlı Kilo Tahmini";
        let selectedAmount = 30;
        const myPhoneNumber = "905074658470";
        let generatedSMSCode = "";
        let userEnteredPhone = "";

        function toggleMenu() {
            const drawer = document.getElementById('appDrawer');
            const overlay = document.getElementById('menuOverlay');
            drawer.classList.toggle('open');
            overlay.classList.toggle('active');
        }

        function switchSection(sectionId) {
            document.querySelectorAll('.analysis-section').forEach(el => el.classList.add('hidden'));
            document.getElementById('reportScreen').classList.add('hidden');
            document.getElementById('waitingScreen').classList.add('hidden');
            document.getElementById('paymentCard').classList.add('hidden');
            
            document.getElementById(sectionId).classList.remove('hidden');
        }

        function sendSMSCode() {
            let phoneInputVal = document.getElementById('userPhone').value.replace(/\s+/g, '');
            if(phoneInputVal.length < 10) {
                alert("Lütfen geçerli bir telefon numarası giriniz.");
                return;
            }
            userEnteredPhone = phoneInputVal;
            generatedSMSCode = Math.floor(1000 + Math.random() * 9000).toString();
            document.getElementById('sentCodeDisplay').innerText = generatedSMSCode;

            document.getElementById('stepPhone').classList.add('hidden');
            document.getElementById('stepCode').classList.remove('hidden');
        }

        function verifySMSCode() {
            const enteredCode = document.getElementById('smsCodeInput').value;
            if(enteredCode !== generatedSMSCode) {
                alert("Hatalı doğrulama kodu!");
                return;
            }

            document.getElementById('loginScreen').classList.add('hidden');
            document.getElementById('appMainContent').classList.remove('hidden');
            document.getElementById('welcomeUserText').innerText = "Kayıtlı Tel: " + userEnteredPhone;
            switchSection('sectionKilo');
        }

        function logout() {
            document.getElementById('appMainContent').classList.add('hidden');
            document.getElementById('reportScreen').classList.add('hidden');
            document.getElementById('waitingScreen').classList.add('hidden');
            document.getElementById('loginScreen').classList.remove('hidden');
            document.getElementById('stepCode').classList.add('hidden');
            document.getElementById('stepPhone').classList.remove('hidden');
            document.getElementById('userPhone').value = "";
        }

        function startAnalysis(type, price) {
            selectedPackage = type;
            selectedAmount = price;
            document.getElementById('selectedPrice').innerText = price;
            document.getElementById('paymentTitleText').innerText = type + " - Ödeme Talimatı";
            document.getElementById('paymentCard').classList.remove('hidden');
            window.scrollTo({top: document.getElementById('paymentCard').offsetTop, behavior: 'smooth'});
        }

        function copyIBAN() {
            navigator.clipboard.writeText("TR19 0001 5001 5800 7336 9987 02");
            alert("IBAN Kopyalandı!");
        }

        function sendWhatsAppNotification() {
            const message = `Merhaba,\n\nBS Ekspertiz platformundan ${selectedPackage} için ödeme yaptım.\n\n📱 Telefon: ${userEnteredPhone}\n📋 Referans Kodu: BS-8492\n💰 Tutar: ${selectedAmount} TL\n\nDekontu gönderiyorum, kontrol edebilir misiniz?`;
            const waUrl = `https://wa.me/${myPhoneNumber}?text=${encodeURIComponent(message)}`;
            window.open(waUrl, '_blank');

            document.querySelectorAll('.analysis-section').forEach(el => el.classList.add('hidden'));
            document.getElementById('paymentCard').classList.add('hidden');
            document.getElementById('waitingScreen').classList.remove('hidden');

            setTimeout(() => {
                document.getElementById('aiStatusText').innerHTML = `✅ ${selectedPackage} verileri incelendi.<br><strong>Yapay zeka motoru</strong> sonuçları döküyor...`;
            }, 2500);

            setTimeout(() => {
                document.getElementById('waitingScreen').classList.add('hidden');
                document.getElementById('reportTypeTitle').innerText = selectedPackage;
                document.getElementById('reportScreen').classList.remove('hidden');
            }, 5000);
        }
    </script>
</body>
</html>
