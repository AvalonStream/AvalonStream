# Avalon

### พีซี Windows 10/11 x64 หนึ่งเครื่อง เดสก์ท็อปอิสระหลายชุด

Avalon เปลี่ยนโฮสต์ Windows 10/11 x64 หนึ่งเครื่องให้เป็นอินสแตนซ์เดสก์ท็อปหลายชุดที่เข้าถึงแยกจากกันได้ แต่ละอินสแตนซ์สามารถมี Windows session, จอเสมือน, input, audio, แอป, เกม และการเชื่อมต่อ Moonlight ของตัวเอง

**หนึ่งโฮสต์ หลายอินสแตนซ์**

[English](README.md)

[Development log และข้อเสนอแนะ](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md) · [Issues / บั๊กและคำขอฟีเจอร์](https://github.com/AvalonStream/AvalonStream/issues)

---

## Avalon คืออะไร?

Avalon คือแพลตฟอร์มสตรีมเดสก์ท็อปแบบหลายเซสชันสำหรับ Windows 10/11 x64 แทนที่จะให้ทั้งเครื่องรองรับเดสก์ท็อปโต้ตอบเพียงชุดเดียว Avalon ช่วยให้ Windows หลายอินสแตนซ์ทำงานพร้อมกันบนโฮสต์เดียวโดยไม่ต้องใช้ virtual machine เต็มรูปแบบสำหรับผู้ใช้แต่ละคน

---

## ความสามารถหลัก

- Windows หลายอินสแตนซ์ที่เป็นอิสระบนโฮสต์เดียว
- บริบทการสตรีมแยกสำหรับแต่ละอินสแตนซ์
- จอเสมือน ความละเอียด และ refresh rate แยกต่ออินสแตนซ์
- เส้นทาง keyboard, mouse และ session audio แยกจากกัน
- Avalon ดูแลวงจรชีวิตของ session โดยไม่ต้องเปิด RDP client ภายนอกค้างไว้
- สร้าง จับคู่ ตรวจสอบสถานะ และวินิจฉัยผ่าน Web
- Moonlight ยังคงเป็น client บนโทรศัพท์ แท็บเล็ต TV และ PC

---

## ทำงานอย่างไร

สร้างอินสแตนซ์ เลือกการตั้งค่าจอ และจับคู่ client จากนั้น Avalon จะเตรียม Windows session, จอเสมือน, บริบทการสตรีม และวงจรชีวิต ก่อนเชื่อมต่อผ่าน Moonlight

```text
Windows 10/11 x64 Host
        │
      Avalon
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Instance 01  Instance 02  Instance 03
 │      │      │
 ▼      ▼      ▼
Moonlight  Moonlight  Moonlight
```

---

## ออกแบบมาสำหรับ Moonlight

Avalon เปลี่ยนฝั่งโฮสต์ ไม่ได้บังคับให้เปลี่ยน client ที่คุ้นเคย Moonlight ยังใช้ได้บน Windows, Linux, macOS, Android, iOS/iPadOS, Android TV และอุปกรณ์อื่นที่รองรับ

---

## กรณีใช้งานทั่วไป

- เล่นเกมในบ้าน: ผู้ใช้หลายคนใช้อินสแตนซ์ต่างกันพร้อมกัน
- หลายบัญชีและงานแบบ multi-instance
- หลาย remote workstation บนพีซีประสิทธิภาพสูงเครื่องเดียว
- การทดสอบ automation และสภาพแวดล้อม compatibility
- Homelab และ remote computing แบบ self-hosted

---

## รูปแบบการแยก

Avalon ให้การแยกระดับ Windows session ไม่ใช่การแยกแบบ virtual machine เต็มรูปแบบ Desktop, แอป, จอ, input และ audio แยกกันตามอินสแตนซ์ แต่ยังใช้ Windows host, kernel, CPU, GPU และฮาร์ดแวร์จริงร่วมกัน จึงไม่ควรถือเป็นขอบเขตความปลอดภัยระดับ VM

---

## แพลตฟอร์มและประสิทธิภาพ

Avalon รองรับ Windows 10 และ Windows 11 แบบ 64 บิต ความละเอียด refresh rate codec HDR และจำนวนอินสแตนซ์พร้อมกันขึ้นอยู่กับ GPU, driver, encoder, เครือข่าย และฮาร์ดแวร์ client

---

## สถานะโครงการ

Avalon อยู่ในระยะ Alpha อินเทอร์เฟซ ความเข้ากันได้ และส่วนประกอบระดับล่างยังมีการเปลี่ยนแปลง จึงอาจมี breaking changes และปัญหาเฉพาะฮาร์ดแวร์

---

## การพัฒนาและข้อเสนอแนะ

README นี้เป็นคำแนะนำผลิตภัณฑ์ที่คงที่ ส่วนความคืบหน้าการพัฒนาแบบเรียลไทม์และแนวทางการฝากข้อความจะแยกไว้ใน development log

- [Development log และข้อเสนอแนะ](https://github.com/AvalonStream/AvalonStream/blob/main/devlog.md)
- [Issues / บั๊กและคำขอฟีเจอร์](https://github.com/AvalonStream/AvalonStream/issues)

**หนึ่งโฮสต์ หลายอินสแตนซ์**
