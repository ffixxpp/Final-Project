# Final-Project
<h1>ระบบเปิดปิดกั้นรถโดยใช้คีย์การ์ด IOT </h1>
<h2>การเข้าออกของพนักงานร้านอาหาร</h2>
<h4>สมาชิกในกลุ่ม</h4>
<p>64108657 ปาลิตา อาจบำรุง</p> 
<p>64108673 ปิ่นสุดา จรเทพ</p> 
<p>64121080 อาภัสรา โสดาพัฒน์</p> 
<h3>บทนำ</h3>
<p>ปัจจุบันเทคโนโลยีมีความก้าวหน้าและเติบโตอย่างรวดเร็ว การพัฒนาเทคโนโลยีสำหรับควบคุมการเข้าออกในปัจจุบันนี้มีความสำคัญยิ่งในการเพิ่มประสิทธิภาพและความปลอดภัยและความสะดวกสบาย ทางกลุ่มของผู้จัดทำได้มองเห็นถึงความสำคัญเรื่องความปลอดภัยและความสะดวกสบายจึงได้มุ่งเน้นในการทำระบบเปิดปิดกั้นรถโดยใช้คีย์การ์ด IoT การเข้าออกของพนักงานโดยไม่ต้องมานั่งเช็คเอง ทำให้กระบวนการนี้มีประสิทธิภาพและความปลอดภัยมากขึ้น</p>
<p>ทางกลุ่มผู้จัดทำจึงมุ่งเน้นในการทำระบบช่วยแก้ปัญหาเกี่ยวกับการเช็คการเข้า-ออกของพนักงานร้านอาหาร โดยมีการแสดงผลจากการสแกนบัตรผ่านสู่หน้าเว็บ จะแสดงรหัสพนักงานวันที่และเวลา ผ่านอุปกรณ์ IoTเพื่อแสดงให้เห็นการเข้าออกของพนักงานในร้านอาหาร การประยุกต์ใช้ IoT ช่วยผู้ใช้สามารถตรวจสอบข้อมูลการเข้า-ออกของพนักงานได้และการติดตามพฤติกรรมของพนักงานอีกด้วย</p>
<p>การใช้ระบบเปิดปิดกั้นรถโดยใช้คีย์การ์ด IOT มีวัตถุประสงค์ช่วยแก้ปัญหาเกี่ยวกับการเช็คการเข้า-ออกของพนักงานร้านอาหารด้วยมือ ระบบนี้ไม่เพียงทำให้การเข้า-ออกเป็นเรื่องรวดเร็วและสะดวก นอกจากนี้ยังเพิ่มระดับความปลอดภัยด้วยการควบคุมการเข้าถึงที่มีประสิทธิภาพ</p>
<h3>การออกแบบระบบ</h3>
<h4>สถาปัตยกรรมระบบ</h4>
<img src=https://github.com/ffixxpp/Final-Project/blob/main/%E0%B8%AA%E0%B8%96%E0%B8%B2%E0%B8%9B%E0%B8%B1%E0%B8%95%E0%B8%A2%E0%B8%81%E0%B8%A3%E0%B8%A3%E0%B8%A1%E0%B8%A3%E0%B8%B0%E0%B8%9A%E0%B8%9A.png>
<p>จากสถาปัตยกรรมระบบนี้ </p>
<p>โมดูลที่ 1 เริ่มจากการแสกน Key card ซึ่งเมื่อนำไปใกล้โมดูล RFID จะถูกอ่านและนำข้อมูลไปใช้งานต่อไป  ซึ่ง RFID รับข้อมูลจากคีย์การ์ด ส่งไปที่บอร์ด บอร์ดสั่งให้ไม้กานทำการเปิดประตูกั้น </p>
<p>โมดูลที่ 2 จะเป็นการทำงานของ MQTT Broker โดยตัวบอร์ดจะทำการส่งข้อมูลพนักงาน ซึ่งมาจากข้อมูลในคีย์การ์ด โดยมีการจัดเก็บฐานข้อมูล DB Server หรือเซิร์ฟเวอร์ฐานข้อมูลที่จะเก็บข้อมูลที่ได้รับจากโมดูล ESP8266 ผ่าน MQTT Broker</p>
<p>โมดูลที่ 3 ข้อมูลเหล่านี้จะถูกนำไปแสดงผลหรือใช้งานผ่าน Web เพื่อการตรวจสอบ, การควบคุมหรือการวิเคราะห์ ทำให้ผู้ใช้สามารถเข้าถึงและจัดการกับข้อมูลที่ได้รับจากอุปกรณ์ IoT ได้จากทุกที่ที่มีการเชื่อมต่ออินเทอร์เน็ต</p>
<h4>สถาปัตยกรรมซอฟแวร์</h4>
<h3>โครงสร้างข้อมูล</h3>
<p>ข้อมูลที่ถูกอ่านจากคีย์การ์ดโดยโมดูล RFID RC522 จะถูกจัดเก็บและแปลงรูปเป็นรูปแบบ JSON ซึ่ประกอบด้วยรายละเอียดเช่น รหัสพนักงาน, วันที่, และเวลาที่ทำการอ่านคีย์การ์ดนั้น ๆ</p>
<pre>
"83db35f": [
    {
      "topic": "83db35f",
      "payload": "Detect",
      "status": "out",
      "timestamp": "2023-12-24 21:58:35",
      "id": 2
    }
</pre>
<h3>Data Dictionary</h3>

| Attribute Name | Description      | Data Type | Example             |
|----------------|------------------|-----------|---------------------|
| topic          | ID เจ้าของรถ      | varchar   | 83db35f             |
| payload        | ตรวจจับบัตร        | varchar   | Detect              |
| status         | การเข้า-ออก       | varchar   | out                 |
| timestamp      | วันเวลา           | datetime  | 2023-12-24 21:58:35 |
| id             | ID ของข้อมูลที่นำเข้า | int       | 1                   |

<h3>การพัฒนาระบบ</h3>
<h4>Board</h4>
<p>1.ESP8266 ทำหน้าที่ในการรับค่ามาจาก FRID </p>
<h4>Sensor</h4>
<p>1.	RFID-RC522 รับข้อมูลจากคีย์การ์ด </p>
<p>2.	Servo SG90 ทำหน้าที่เปิดประตูกั้น</p>
<h4>เครื่องมือ</h4>
<p>1.	ภาษา C ใช้เขียนในการรับค่าข้อมูลและส่งข้อมูลของอุปกรณ์ Microcontroller </p>
<p>2.	Python ใช้ในการเขียน API ในระบบหลังบ้าน </p>
<p>3.	HTML สร้างโครงสร้างเนื้อหาบน Website</p>
<p>4.	CSS  เป็นการตกแต่ง Website</p>
<p>5.	JSON server ในการเก็บข้อมูล</p>
<h4>ไลบารี่</h4>
<p>1. ESP8266WiFi: ไลบรารีสำหรับใช้กับ ESP8266 เพื่อเชื่อมต่อกับ Wi-Fi network</p>
<p>2. MFRC522: ไลบรารีสำหรับใช้อ่าน RFID โดยใช้โมดูล MFRC522</p>
<p>3. Servo: ไลบรารีสำหรับควบคุม Servo Motor เพื่อควบคุมการหมุนหรือการเคลื่อนไหว</p>
<p>4. PubSubClient: ไลบรารีสำหรับใช้กับ MQTT (Message Queuing Telemetry Transport) protocol, ทำให้ ESP8266 สามารถส่งและรับข้อมูลผ่านโปรโตคอล MQTT ได้</p>
<h3>การทดสอบ</h3>
<h3>สรุปผลการทดสอบ</h3>


















