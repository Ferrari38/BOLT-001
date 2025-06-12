# Daily Income Calculator (คำนวณรายได้ประจำวัน)
เว็บแอปพลิเคชันขนาดเล็กสำหรับคำนวณรายรับ-รายจ่ายรายวันของผู้ขับขี่บริการรถโดยสาร เช่น GRAB,BOLT และงานนอก

[![เปิดใช้งานแอป](https://img.shields.io/badge/🚀-เปิดใช้งานแอป-2ea44f?style=for-the-badge)](https://ferrari38.github.io/daily-income-calculator/)

---

## 📋 คุณสมบัติ

- บันทึกรายรับจาก GRAB, BOLT, ทิป และรายรับอื่นๆ
- หักค่าคอมมิชชั่น 18% จาก BOLT โดยอัตโนมัติ
- คำนวณค่าซ่อมบำรุง 10%
- บันทึกค่าน้ำมันและค่าใช้จ่ายเพิ่มเติม
- คำนวณรายได้สุทธิ
- คำนวณรายได้หาร 2 + ค่าซ่อม
- คำนวณค่าเฉลี่ย “บาทต่อกิโลเมตร” จากรายได้รวมก่อนหักค่าคอม

## 📦 วิธีใช้งาน

[![เปิดใช้งานแอป](https://img.shields.io/badge/🚀-เปิดใช้งานแอป-2ea44f?style=for-the-badge)](https://ferrari38.github.io/daily-income-calculator/)

1. คลิกปุ่มด้านบนเพื่อเข้าใช้งานแอป
2. หรือดาวน์โหลดไฟล์ HTML แล้วเปิดด้วยเว็บเบราว์เซอร์
3. กรอกข้อมูลในแบบฟอร์ม แล้วคลิก “คำนวณ”

## 🧮 สูตรที่ใช้

- **ค่าคอมมิชชั่น BOLT** = 18% ของรายได้จาก BOLT
- **ค่าซ่อมบำรุง** = 10% ของรายรับ (หลังหักค่าคอม)
- **รายได้สุทธิ** = รายรับ - รายจ่ายทั้งหมด + ทิป
- **บาทต่อกิโลเมตร** = (GRAB + BOLT + ทิป + รายรับอื่นๆ) ÷ ระยะทางที่ใช้

## 💡 เหมาะสำหรับ

- คนขับ Grab / Bolt
- ฟรีแลนซ์ที่ต้องคำนวณรายได้ประจำวัน
- ผู้ที่ต้องการติดตามต้นทุน-กำไรในแต่ละวัน

[![เปิดใช้งานแอป](https://img.shields.io/badge/🚀-เปิดใช้งานแอป-2ea44f?style=for-the-badge)](https://ferrari38.github.io/daily-income-calculator/)


<style>
 header {
  display: none;
 }
  * {
    box-sizing: border-box;
  }

  body {
    font-family: sans-serif;
    padding: 20px;
    background: #f2f2f2;
    margin: 0;
  }

  .container {
    background: white;
    padding: 20px;
    border-radius: 10px;
    max-width: 500px;
    width: 100%;
    margin: auto;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }

  h2 {
    font-size: 22px;
    color: #003300;
    margin: 0 0 10px;
  }

  h3 {
    margin-top: 20px;
    font-size: 18px;
    color: #004d00;
  }

  label {
    display: block;
    margin-top: 10px;
    font-size: 14px;
  }

  input, button, select {
    width: 100%;
    padding: 12px;
    margin-top: 5px;
    font-size: 16px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }

  button {
    margin-top: 15px;
    cursor: pointer;
    background-color: #28a745;
    color: white;
    border: none;
  }

  button:hover {
    background-color: #218838;
  }

  .result {
    margin-top: 20px;
    background: #e6ffe6;
    padding: 15px;
    border-radius: 5px;
    color: #006600;
    font-size: 14px;
    line-height: 1.6;
  }

  @media (max-width: 400px) {
    h2 {
      font-size: 20px;
    }

    input, button, select {
      font-size: 14px;
      padding: 10px;
    }

    .result {
      font-size: 13px;
    }
  }
</style>
<body>
  <div class="container">
    <h2>คำนวณรายได้ประจำวัน</h2>

    <label>วันที่:</label>
    <input type="date" id="date" />

    <h3>รายรับ</h3>
    <label>รายได้จาก GRAB (บาท):</label>
    <input type="number" id="grab" />

    <label>รายได้จาก BOLT (บาท):</label>
    <input type="number" id="bolt" />

    <label>ทิป (บาท):</label>
    <input type="number" id="tip" />

    <label>รายรับอื่นๆ (บาท):</label>
    <input type="number" id="extraIncome" />

    <h3>รายจ่าย</h3>
    <label>ค่าน้ำมัน (บาท):</label>
    <input type="number" id="oil" />

    <label>รายจ่ายอื่นๆ (บาท):</label>
    <input type="number" id="otherExpense" />

    <h3>ระยะทางที่ใช้</h3>
    <label>เริ่มงาน (กม.):</label>
    <input type="number" id="startKm" />

    <label>เลิกงาน (กม.):</label>
    <input type="number" id="endKm" />
    <label>หรือ:</label>

    <label>ระยะทางที่ใช้ (กม.):</label>
    <input type="number" id="distance1" />
    

    <button onclick="calculate()">คำนวณ</button>
    <button onclick="resetForm()">ล้างข้อมูล</button>

    <div class="result" id="result"></div>
  </div>

  <script>
    function calculate() {
      const date = document.getElementById('date').value;
      const grab = parseFloat(document.getElementById('grab').value) || 0;
      const bolt = parseFloat(document.getElementById('bolt').value) || 0;
      const tip = parseFloat(document.getElementById('tip').value) || 0;
      const extraIncome = parseFloat(document.getElementById('extraIncome').value) || 0;
      const oil = parseFloat(document.getElementById('oil').value) || 0;
      const otherExpense = parseFloat(document.getElementById('otherExpense').value) || 0;
      const startKm = parseFloat(document.getElementById('startKm').value) || 0;
      const endKm = parseFloat(document.getElementById('endKm').value) || 0;
      const distance = parseFloat(document.getElementById('distance1').value) || 0;

      const distance = endKm - startKm;
      if (distance < 0) {
        alert("กรุณากรอกเลขกิโลเมตรให้ถูกต้อง (เลิกงานต้องมากกว่าเริ่มงาน)");
        return;
      }

      const totalIncomeBeforeCommission = grab + bolt + tip + extraIncome;

      const boltCommission = bolt * 0.18;
      const boltAfter = bolt - boltCommission;
      const totalIncomeBeforeMaintenance = grab + boltAfter + extraIncome;
      const maintenance = totalIncomeBeforeMaintenance * 0.10;

      const totalExpenses = oil + otherExpense + maintenance;
      const netIncome = totalIncomeBeforeMaintenance - totalExpenses + tip;

      const halfIncomePlusMaintenance = (netIncome / 2 + maintenance).toFixed(2);
      const costPerKm = distance > 0 ? (totalIncomeBeforeCommission / distance).toFixed(2) : "0.00";
      const costPerKm1 = distance1 > 0 ? (totalIncomeBeforeCommission / distance1).toFixed(2) : 0;
     

      const format = n => n.toLocaleString(undefined, { minimumFractionDigits: 2 });

      const resultHTML = `
        <strong>สรุปผลประจำวันที่: ${date}</strong><br><br>
        <strong>รายรับ</strong><br>
        GRAB: ${format(grab)} บาท<br>
        BOLT: ${format(bolt)} บาท (หัก 18%: ${format(boltCommission)} บาท เหลือ: ${format(boltAfter)} บาท)<br>
        รายรับอื่นๆ: ${format(extraIncome)} บาท<br>
        ทิป: ${format(tip)} บาท<br>
        รวมรายรับก่อนหักค่าคอมมิชชั่น: ${format(totalIncomeBeforeCommission)} บาท<br>
        รวมรายรับก่อนหักค่าซ่อม: ${format(totalIncomeBeforeMaintenance)} บาท<br><br>

        <strong>รายจ่าย</strong><br>
        ค่าซ่อม 10%: ${format(maintenance)} บาท<br>
        ค่าน้ำมัน: ${format(oil)} บาท<br>
        รายจ่ายอื่นๆ: ${format(otherExpense)} บาท<br>
        <strong>ค่าคอมมิชชั่น BOLT:<strong> ${format(boltCommission)} บาท<br>
        <strong>รวมรายจ่ายทั้งหมด:<strong> ${format(totalExpenses)} บาท<br><br>

        <strong>รายได้สุทธิ:</strong> ${format(netIncome)} บาท<br>
        <strong>ทิป:<strong> ${format(tip)} บาท<br>
        <strong>หาร 2 + ค่าซ่อม:</strong> ${halfIncomePlusMaintenance} บาท<br><br>

        ระยะทางที่ใช้:${distance} กม.<br>
        บาทต่อกิโลเมตร:${costPerKm} บาท/กม.
        <strong>หรือ:</strong>
        ระยะทางที่ใช้:${distance} กม.<br>
        บาทต่อกิโลเมตร:${costPerKm} บาท/กม.
      `;

      document.getElementById('result').innerHTML = resultHTML;
    }

    function resetForm() {
      document.querySelectorAll('input').forEach(input => input.value = '');
      document.getElementById('result').innerHTML = '';
    }
  </script>
</body>
