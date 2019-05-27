# Day 1

### Cloud Native
- ธุรกิจต้องการการส่งมอบอย่างต่อเนื่อง
- DevOps เป็นวัฒนธรรมองค์กร
- UAT ต้องใช้ user จริงทำ และห้ามบอกว่าคลิกตรงไหน
- Microservice มีข้อเสียถ้าไม่เข้าใจหลักการ

### ปัญหาของระบบแบบ Monolith
- ตรงกลางล่มตายหมด
- ส่วนใหญ่จะแบ่งเป็น layers เช่น Frontend, Backend, Database
- ระบบ Legacy จะแก้ไขยาก กระทบหลายส่วน
- ปัญหามักถูกดองไว้ เพราะทีมต้องการแค่รันให้ทันเวลา
- แต่ละ Module ไม่แยกเป็นอิสระจากกัน 
- มี Common Module ที่แชร์กันไปเยอะ ทำให้เวลาแก้แล้วกระทบหลายส่วน
- ใน Database มี tables เยอะเกิน แต่ละ table มี fields เยอะเกิน (เคยมีตัวอย่าง 3,000 fields เผื่อไว้เติม field ไม่ต้องการ alter เพราะมันเป็น cost)
- คนพัฒนามีอายุการทำงานโค้ดน้อย เพราะเติบโตไปทำส่วนอื่น และเน้นประชุมเยอะขึ้น
- บางครั้งปัญหาเกิดจากการ Update Firmware ของ Database
- Do all modules need to use the same Database, Language and Runtime .. ?

### SOA (Service-Oriented Architecture)
- แนวคิดคือส่งมอบ Software ที่ดีอย่างยั่งยืน http://soa-manifesto.org
- Focus ที่ Business value ไม่ใช่เทคนิค
- Focus ที่ความยืดหยุ่นมากกว่า
- ออกแบบ Architecture ให้อยู่ได้นานที่สุด (แต่มันไม่มีจริงหรอก 😂)
- Architecture ที่ดีสามารถปรับปรุงได้อย่างต่อเนื่อง
- Shared service อะไรที่เหมือนกันจะเอามารวมกัน
- มี Organize องค์กรที่ซับซ้อน
- Business service ไม่สามารถ Reuse ได้
- Enterprise service จะมีขนาดใหญ่ ต้องใช้ Application service
- Application service ต้องพึ่ง Inflastucture service
- เกิดตำแหน่ง Project Manager เพื่อมาจัดการ Coordination across all teams (Cost เพิ่มอีกแล้ว)
- มี layer หลายชั้นกว่าจะถึง core service (หัวหอม architecture 😅)

### Service ที่ดีที่สุด
- Standalone อยู่ได้ด้วยตัวเอง
- Indipendence ต้องอิสระ
- ให้ Value ทั้ง Business และ IT
- ลด Service ตัวกลาง (Service1 -> Service2 -> Service3)

### Microservice
- มี Services 2 แบบ คือ `Business service` และ `Infrastructure service` ดูแลโดย Application Development Team
- Focus ที่ `Business service` เพื่อดำเนินธุรกิจ แต่ต้องมี `Infrastructure` ที่นิ่ง
- ควรจะ Minimal coordination ลดการจัดการลง (ลด cost ได้ด้วย 😃)
- การปรับใช้ `Microservice` แทน `Monolith` ควรจะทะยอยทำทีละ Service หรือทีะ Module

### ** Notes
- Architecture ที่ดีที่สุดอยู่บน Production นั่นและ!!
- ยิ่งมี standard เยอะยิ่ง cost เยอะ
- การโอนเงินสำหรับธนาคารเป็น Infra service เพราะเป็น core
- Netflix ใช้ AWS เป็นหลัก (ทำ AWS ล่มในช่วงแรก)
