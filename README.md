# Drone API Server (Assignment #1)

API Server สร้างด้วย **Node.js + Express.js** ทำหน้าที่เป็นตัวกลางระหว่างหน้าเว็บ
กับเซิร์ฟเวอร์ 2 ตัว

- **Server 1 (Drone Config Server):** เก็บข้อมูล config และสถานะของโดรน
- **Server 2 (Drone Log Server / PocketBase):** เก็บ log อุณหภูมิของโดรน

**Deployment:** `<http://assignment1webapp.onrender.com>`

## วิธี run บนเบราว์เซอร์
1. เปิดเบราว์เซอร์แล้วพิมพ์
   ```
   http://assignment1webapp.onrender.com/configs/67010999
   ```
   ```
   http://assignment1webapp.onrender.com/status/67010999
   ```
   ```
   http://assignment1webapp.onrender.com/logs/67010999
   ```

## วิธี run ในเครื่อง

1. ติดตั้ง Node.js 18 ขึ้นไป
2. เปิดโฟลเดอร์ใน VS code แล้วสร้าง terminal โดยใช้ command prompt แล้วรัน `npm install`
3. สร้างไฟล์ `.env` ในโฟล์เดอร์เดียวกัน แล้วใส่ค่าจริง
   ```
   PORT=3000
   CONFIG_URL=<URL ของ Drone Config Server>
   LOG_URL=<URL ของ Drone Log Server>
   LOG_API_TOKEN=<Bearer token>
   ```
4. `npm start`
5. เปิดเบราว์เซอร์แล้วพิมพ์ 
   ```
   http://localhost:3000/configs/67010999
   ```
   ```
   http://localhost:3000/status/67010999
   ```
   ```
   http://localhost:3000/logs/67010999
   ```

## ตัวอย่าง: GET/configs/67010999
```
json
   {
    "drone_id": 67010999, 
    "drone_name": "...", 
    "light": "...", 
    "country": "...", 
    "weight": 0 
   }
```

## Deploy (Render)

1. New + → Web Service เลือก repo นี้
2. Build Command: `npm install` / Start Command: `npm start`
3. ที่หน้า Environment เพิ่ม `CONFIG_URL`, `LOG_URL`, `LOG_API_TOKEN`
