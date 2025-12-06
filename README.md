<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>صندوق التكافل الاجتماعي - caisse solidarité</title>
  <link rel="icon" type="image/x-icon" href="https://drive.google.com/uc?export=view&id=1fZ-qUIcf9bD-BZlXfV1aT7TzcqSZp4uq">
  <meta name="description" content="صندوق التكافل الاجتماعي - نظام إدارة المستحقات المالية">
  <style>
    :root {
      --bg-color: #f5f7fa;
      --text-color: #222;
      --card-color: #fff;
      --footer-color: #555;
      --primary-color: #007bff;
      --success-color: #28a745;
      --danger-color: #dc3545;
      --warning-color: #ffc107;
    }

    body.dark {
      --bg-color: #121212;
      --text-color: #f1f1f1;
      --card-color: #1e1e1e;
      --footer-color: #aaa;
    }

    * {
      box-sizing: border-box;
    }

    body {
      font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      color: var(--text-color);
      display: flex;
      flex-direction: column;
      align-items: center;
      min-height: 100vh;
      margin: 0;
      padding: 20px;
      transition: background-color 0.3s, color 0.3s;
    }

    body.dark {
      background: linear-gradient(135deg, #2c3e50 0%, #3498db 100%);
    }

    .container {
      background: var(--bg-color);
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 15px 35px rgba(0,0,0,0.1);
      width: 100%;
      max-width: 800px;
      margin: 20px 0;
      position: relative;
    }

    header {
      text-align: center;
      margin-bottom: 30px;
    }

    .logo {
      width: 120px;
      height: 120px;
      border-radius: 50%;
      margin: 0 auto 15px;
      overflow: hidden;
      border: 4px solid var(--primary-color);
      box-shadow: 0 5px 15px rgba(0,0,0,0.2);
    }

    .logo img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    h1 {
      font-size: 1.6em;
      margin: 10px 0 5px 0;
      color: var(--primary-color);
    }

    h2 {
      font-size: 1em;
      margin: 0;
      color: #777;
      font-weight: normal;
    }

    h3 {
      font-size: 1.2em;
      margin: 20px 0 15px 0;
      color: var(--primary-color);
      text-align: center;
      border-bottom: 2px solid var(--primary-color);
      padding-bottom: 8px;
    }

    .toggle-mode {
      position: absolute;
      top: 20px;
      left: 20px;
      background: var(--card-color);
      border: none;
      font-size: 1.3em;
      cursor: pointer;
      color: var(--text-color);
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      transition: all 0.3s;
    }

    .toggle-mode:hover {
      transform: scale(1.1);
    }

    .search-box {
      text-align: center;
      margin: 20px 0;
    }

    .input-group {
      display: flex;
      gap: 10px;
      margin-bottom: 15px;
    }

    input {
      padding: 15px;
      border-radius: 12px;
      border: 2px solid #ddd;
      width: 100%;
      text-align: center;
      font-size: 1.1em;
      background: var(--card-color);
      color: var(--text-color);
      transition: border-color 0.3s;
    }

    input:focus {
      outline: none;
      border-color: var(--primary-color);
    }

    button {
      padding: 15px 25px;
      border: none;
      background: linear-gradient(135deg, #007bff, #0056b3);
      color: white;
      border-radius: 12px;
      font-size: 1em;
      cursor: pointer;
      transition: all 0.3s;
      font-weight: bold;
      white-space: nowrap;
    }

    button:hover {
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(0,123,255,0.3);
    }

    button:active {
      transform: translateY(0);
    }

    .card {
      background: var(--card-color);
      border-radius: 16px;
      padding: 25px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.1);
      text-align: right;
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.4s ease;
      border: 1px solid rgba(0,0,0,0.05);
      margin-bottom: 20px;
    }

    .card.show {
      opacity: 1;
      transform: translateY(0);
    }

    .amount {
      font-size: 1.4em;
      font-weight: bold;
      margin: 15px 0;
      padding: 15px;
      border-radius: 12px;
      transition: all 0.3s;
      text-align: center;
    }

    .positive {
      color: var(--success-color);
      background: rgba(40, 167, 69, 0.1);
      border: 2px solid var(--success-color);
    }

    .negative {
      color: var(--danger-color);
      background: rgba(220, 53, 69, 0.1);
      border: 2px solid var(--danger-color);
    }

    .neutral {
      color: var(--text-color);
      background: rgba(0, 0, 0, 0.05);
      border: 2px solid #ddd;
    }

    .info-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin: 15px 0;
      padding: 12px 0;
      border-bottom: 1px solid rgba(0,0,0,0.1);
    }

    .info-label {
      font-weight: bold;
      color: var(--text-color);
    }

    .info-value {
      color: var(--text-color);
      font-size: 1.1em;
    }

    .monthly-contributions {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
      gap: 15px;
      margin-top: 20px;
    }

    .month-box {
      background: var(--card-color);
      border-radius: 12px;
      padding: 15px;
      text-align: center;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      border: 2px solid #e9ecef;
      transition: all 0.3s;
    }

    .month-box:hover {
      transform: translateY(-3px);
      box-shadow: 0 6px 15px rgba(0,0,0,0.12);
    }

    .month-name {
      font-weight: bold;
      font-size: 1.1em;
      margin-bottom: 10px;
      color: var(--primary-color);
    }

    .month-amount {
      font-size: 1.2em;
      font-weight: bold;
      padding: 8px;
      border-radius: 8px;
    }

    .paid {
      background: rgba(40, 167, 69, 0.15);
      color: var(--success-color);
      border: 1px solid var(--success-color);
    }

    .not-paid {
      background: rgba(220, 53, 69, 0.15);
      color: var(--danger-color);
      border: 1px solid var(--danger-color);
    }

    .partial {
      background: rgba(255, 193, 7, 0.15);
      color: var(--warning-color);
      border: 1px solid var(--warning-color);
    }

    .loading {
      color: var(--primary-color);
      text-align: center;
      padding: 20px;
    }

    .error {
      color: var(--danger-color);
      text-align: center;
      padding: 20px;
      background: rgba(220, 53, 69, 0.1);
      border-radius: 12px;
      border: 1px solid var(--danger-color);
    }

    .success {
      color: var(--success-color);
    }

    .section-title {
      background: linear-gradient(135deg, var(--primary-color), #0056b3);
      color: white;
      padding: 12px 20px;
      border-radius: 10px;
      margin: 25px 0 15px 0;
      text-align: center;
      font-size: 1.1em;
      font-weight: bold;
    }

    footer {
      text-align: center;
      padding: 20px;
      font-size: 0.8em;
      color: white;
      margin-top: auto;
    }

    @media (max-width: 768px) {
      .container {
        padding: 20px;
        margin: 10px;
      }
      
      .input-group {
        flex-direction: column;
      }
      
      button {
        width: 100%;
      }
      
      .logo {
        width: 100px;
        height: 100px;
      }
      
      .monthly-contributions {
        grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
        gap: 10px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <button class="toggle-mode" onclick="toggleDarkMode()" title="تبديل الوضع">🌙</button>
    
    <header>
      <div class="logo">
        <img src="https://drive.google.com/uc?export=view&id=1fZ-qUIcf9bD-BZlXfV1aT7TzcqSZp4uq" alt="شعار صندوق التكافل الاجتماعي" onerror="handleImageError(this)">
      </div>
      <h1>صندوق التكافل الاجتماعي</h1>
      <h2>caisse solidarité</h2>
    </header>

    <div class="search-box">
      <div class="input-group">
        <input type="number" id="serial" placeholder="أدخل الرقم التسلسلي" onkeypress="handleKeyPress(event)">
        <button onclick="searchData()">بحث</button>
      </div>
    </div>

    <div id="result" class="card"></div>
    <div id="monthlyContributions" class="card" style="display: none;"></div>
  </div>

  <footer>
    جميع الحقوق محفوظة © صندوق التكافل الاجتماعي — caisse solidarité 2025
  </footer>

  <script>
    // رابط Google Sheets الحقيقي
    const SHEET_ID = "1sFcCssl_tF8Ufi5fCgFWe9ok5R2v-lE5H__aEDgSMfo";
    const SHEET_URL = `https://docs.google.com/spreadsheets/d/${SHEET_ID}/gviz/tq?tqx=out:json`;

    // ترتيب الأشهر حسب الطلب
    const orderedMonths = ["أغسطس", "سبتمبر", "أكتوبر", "نوفمبر", "ديسمبر", "يناير", "فبراير", "مارس", "أبريل", "مايو", "يونيو", "يوليو"];

    function handleImageError(img) {
      img.style.display = 'none';
      img.parentElement.innerHTML = `
        <div style="width:120px; height:120px; border-radius:50%; background:linear-gradient(135deg, #007bff, #0056b3); display:flex; align-items:center; justify-content:center; margin:0 auto 15px; color:white; font-size:2em;">
          🤝
        </div>
      `;
    }

    function handleKeyPress(event) {
      if (event.key === 'Enter') {
        searchData();
      }
    }

    async function searchData() {
      const serial = document.getElementById('serial').value.trim();
      const resultDiv = document.getElementById('result');
      const monthlyDiv = document.getElementById('monthlyContributions');
      
      resultDiv.classList.remove('show');
      monthlyDiv.style.display = 'none';

      if (!serial) {
        showResult("الرجاء إدخال الرقم التسلسلي.", "error");
        return;
      }

      showResult(`
        <div class="loading">
          <p>جاري البحث في السجلات...</p>
          <div style="margin-top:10px;">⏳</div>
        </div>
      `, "loading");

      try {
        const data = await fetchFromGoogleSheets(serial);
        if (data) {
          displayResult(data);
          displayMonthlyContributions(data);
        } else {
          showResult(`
            <div class="error">
              <p>الرقم التسلسلي غير موجود في السجل</p>
              <p style="margin-top:10px;font-size:0.9em;">الرجاء التحقق من الرقم والمحاولة مرة أخرى</p>
            </div>
          `, "error");
        }
      } catch (error) {
        console.error('خطأ في الاتصال:', error);
        await searchInSampleData(serial);
      }
    }

    async function fetchFromGoogleSheets(serial) {
      try {
        const response = await fetch(SHEET_URL);
        if (!response.ok) {
          throw new Error('فشل في جلب البيانات من الخادم');
        }
        
        const text = await response.text();
        const jsonString = text.substring(47).slice(0, -2);
        const data = JSON.parse(jsonString);
        
        const rows = data.table.rows;
        
        for (let row of rows) {
          const rowData = row.c.map(cell => cell ? (cell.v || '') : '');
          
          if (rowData[1] && rowData[1].toString().trim() === serial.toString().trim()) {
            const monthlyData = {};
            const monthColumns = rowData.slice(3);
            
            monthColumns.forEach((amount, index) => {
              if (index < orderedMonths.length) {
                monthlyData[orderedMonths[index]] = parseFloat(amount) || 0;
              }
            });
            
            return {
              name: rowData[0] || "غير معروف",
              serial: rowData[1] || "غير معروف",
              totalAmount: parseFloat(rowData[2]) || 0,
              monthlyData: monthlyData
            };
          }
        }
        
        return null;
        
      } catch (error) {
        console.error('خطأ في جلب البيانات:', error);
        throw error;
      }
    }

    async function searchInSampleData(serial) {
      const found = sampleData.find(row => row.serial === serial);
      
      if (found) {
        displayResult(found);
        displayMonthlyContributions(found);
        
        setTimeout(() => {
          const additionalInfo = document.createElement('div');
          additionalInfo.innerHTML = `
            <div style="margin-top:15px; padding:10px; background:#fff3cd; border-radius:8px; font-size:0.8em; color:#856404; border:1px solid #ffeaa7;">
              <strong>ملاحظة:</strong> يتم استخدام بيانات تجريبية للعرض. تأكد من اتصال الإنترنت للوصول إلى البيانات الحقيقية.
            </div>
          `;
          document.getElementById('result').appendChild(additionalInfo);
        }, 100);
      } else {
        showResult(`
          <div class="error">
            <p>الرقم التسلسلي غير موجود في السجل</p>
            <p style="margin-top:10px;font-size:0.9em;">الرجاء التحقق من الرقم والمحاولة مرة أخرى</p>
            <div style="margin-top:15px; padding:10px; background:#fff3cd; border-radius:8px; font-size:0.8em; color:#856404;">
              <strong>ملاحظة:</strong> يتم استخدام بيانات تجريبية بسبب مشكلة في الاتصال.
            </div>
          </div>
        `, "error");
      }
    }

    function displayResult(data) {
      const { name, serial, totalAmount, monthlyData } = data;
      
      let amountClass = "neutral";
      let statusText = "";
      
      if (totalAmount < 0) {
        amountClass = "negative";
        statusText = "مدين";
      } else if (totalAmount > 0) {
        amountClass = "positive";
        statusText = "دائن";
      } else {
        statusText = "متوازن";
      }

      // الحصول على قيمة أغسطس
      const augustAmount = monthlyData["أغسطس"] || 0;

      const resultHTML = `
        <div class="section-title">البيانات الأساسية</div>
        
        <div class="info-item">
          <span class="info-label">الإسم:</span>
          <span class="info-value">${name}</span>
        </div>
        
        <div class="info-item">
          <span class="info-label">الرقم التسلسلي:</span>
          <span class="info-value">${serial}</span>
        </div>
        
        <div class="info-item">
          <span class="info-label">إجمالي الدين:</span>
          <span class="info-value" style="font-weight: bold; font-size: 1.1em;">${totalAmount} أوقية</span>
        </div>
        
        <div class="info-item">
          <span class="info-label">رقم الهاتف:</span>
          <span class="info-value" style="font-weight: bold;">${augustAmount} </span>
        </div>
        
        <div class="amount ${amountClass}">
          ${totalAmount} أوقية
        </div>
        
        <div style="margin-top:15px; padding:10px; background:#f8f9fa; border-radius:8px; font-size:0.9em; text-align:center;">
          ${getFinancialAdvice(totalAmount)}
        </div>
      `;
      
      showResult(resultHTML, "success");
    }

    function displayMonthlyContributions(data) {
      const { monthlyData } = data;
      const monthlyDiv = document.getElementById('monthlyContributions');
      
      let contributionsHTML = `
        <div class="section-title">المبالغ المدفوعة حسب الشهر</div>
        <div class="monthly-contributions">
      `;
      
      // عرض الأشهر المطلوبة فقط: سبتمبر، أكتوبر، نوفمبر، ديسمبر
      const targetMonths = ["سبتمبر", "أكتوبر", "نوفمبر", "ديسمبر"];
      
      targetMonths.forEach(monthName => {
        if (monthlyData.hasOwnProperty(monthName)) {
          const amount = monthlyData[monthName];
          let statusClass = "not-paid";
          let statusText = "غير مدفوع";
          let amountDisplay = amount;
          
          if (amount > 0) {
            statusClass = "paid";
            statusText = "مدفوع";
          } else if (amount < 0) {
            statusClass = "partial";
            statusText = "مدفوع جزئياً";
            amountDisplay = Math.abs(amount); // عرض القيمة المطلقة
          }
          
          contributionsHTML += `
            <div class="month-box">
              <div class="month-name">${monthName}</div>
              <div class="month-amount ${statusClass}">${amountDisplay} أوقية</div>
              <div style="margin-top:8px; font-size:0.9em;">${statusText}</div>
            </div>
          `;
        }
      });
      
      contributionsHTML += `</div>`;
      
      monthlyDiv.innerHTML = contributionsHTML;
      monthlyDiv.style.display = 'block';
      monthlyDiv.classList.add('show');
    }

    function getFinancialAdvice(amount) {
      if (amount > 1000) {
        return "💡 ممتاز! لديك رصيد إيجابي جيد";
      } else if (amount > 0) {
        return "💡 جيد، حافظ على هذا المستوى";
      } else if (amount === 0) {
        return "💡 رصيدك متوازن";
      } else if (amount > -300) {
        return "⚠️ لديك مديونية بسيطة يمكنك تسديدها دفعة واحدة";
      } else {
        return "❌ لديك مديونية مرتفعة، يرجى التواصل مع الإدارة";
      }
    }

    function showResult(message, type) {
      const resultDiv = document.getElementById('result');
      resultDiv.innerHTML = message;
      resultDiv.classList.add('show');
    }

    function toggleDarkMode() {
      document.body.classList.toggle('dark');
      const btn = document.querySelector('.toggle-mode');
      btn.textContent = document.body.classList.contains('dark') ? "☀️" : "🌙";
      btn.title = document.body.classList.contains('dark') ? "الوضع النهاري" : "الوضع الليلي";
    }

    // إعدادات أولية
    window.addEventListener('load', function() {
      console.log('تطبيق صندوق التكافل الاجتماعي يعمل بنجاح!');
      console.log('متصل بـ Google Sheets:', SHEET_URL);
    });
  </script>
</body>
</html
