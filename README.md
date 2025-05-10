เราสามารถเขียนเว็บไซต์ที่ดึงข้อมูลจาก GPS ของเครื่องได้ โดยใช้ JavaScript API ที่ชื่อว่า Geolocation API ซึ่งเป็นมาตรฐานของ HTML5
 <h1>ตำแหน่งของคุณ</h1>
  <p id="location">กำลังโหลด...</p>

  <script>
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(
        function(position) {
          document.getElementById('location').textContent =
            'ละติจูด: ' + position.coords.latitude +
            ', ลองจิจูด: ' + position.coords.longitude;
        },
        function(error) {
          document.getElementById('location').textContent =
            'ไม่สามารถดึงตำแหน่งได้: ' + error.message;
        }
      );
    } else {
      document.getElementById('location').textContent =
        'เบราว์เซอร์ไม่รองรับ Geolocation';
    }
  </script>

  หมายเหตุ:
เบราว์เซอร์บนมือถือจะ ถามอนุญาต ก่อนเข้าถึงตำแหน่ง
หากเปิดเว็บผ่าน HTTP (ไม่ใช่ HTTPS) เบราว์เซอร์บางตัวอาจ ไม่อนุญาตให้ใช้ GPS ต้องใช้ HTTPS เท่านั้น
ความแม่นยำของตำแหน่งขึ้นอยู่กับการตั้งค่าของมือถือ (เช่น เปิด GPS อยู่ไหม, ใช้ Wi-Fi หรือข้อมูลมือถือ)
อื่นๆ เราสามารฝัง Google Maps ในหน้าเว็บได้  โดย ต้องมี Google Maps API Key หากยังไม่มี ให้ลงทะเบียนที่ https://console.cloud.google.com และเปิดบริการ Maps JavaScript API และ Geolocation API
