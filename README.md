# RED LAMP - Ways of work between designer and developer

### จุดประสงค์

* สร้างขั้นตอนการทำงานที่ชัดเจนระหว่าง Designer และ Developer
* ลดความสับสนและการตัดสินใจที่เกิดจากการทำงานร่วมกันหลายคน หรือการเข้ามาต่องานจากคนที่เริ่มต้นไว้
* เพิ่มความเร็วของการแก้ไข Theme และการแปลง UI มาเป็น Code

## สารบัญ
* [Designer](#designer)
  - [การเริ่มต้น Project](#การเริ่มต้น-project)
  - [การสร้าง Design systems](#การสร้าง-design-systems)
* [Developer](#developer)
  - [SECTION_NAME](#section-name)
* [Designer & Developer](#designer-&-developer)
  - [SECTION_NAME](#section-name)

## Designer

### การเริ่มต้น Project
* Designer รับ CI (Corporate identity) จาก Customer เพื่อทำการออกแบบ Design concept โดยมีองค์ประกอบ คือ Mood & Tone, Layout และ Component
* หลังจากนำเสนอ, รับ Feedback, แก้ไข และผ่านการยืนยันจาก Customer แล้ว จะเข้าสู่ขั้นตอนการสร้าง Design systems

![Design concept](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/design-concept-presentation.png)

### การสร้าง Design systems
1. Designer สร้าง Variables เพื่อใช้อ้างอิงในงาน Design โดยแบ่งเป็น 3 ระดับ คือ Primitive, Semantic และ Specific
* Primitive : การตั้งชื่อให้กับ Design value เพื่อใช้เรียกเท่านั้น เช่น Color, Typography และ Dimension (Width, Height, Padding, Margin, Gap, Spacing, Border width/radius, Shadow width)

![Primitive color](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variable-primitive-color.png)
![Primitive dimension](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variable-primitive-dimension.png)
![Primitive typography](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variable-primitive-typography.png)

* Semantic : การตั้งชื่อที่มีความหมายให้กับ Design value เพื่อใช้เรียกและสร้างความเข้าใจร่วมกัน เช่น Status color, Content text color, Icon size เป็นต้น

![Semantic color & dimension](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variable-semantic-color-dimension.png)
![Semantic typography](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variable-semantic-typography.png)

* Specific : การตั้งชื่อที่มีความหมายให้กับ Design value เพื่อใช้เรียกและสร้างความเข้าใจร่วมกัน โดยใช้กับ Component หรือ Element ที่กำหนดไว้เท่านั้น เช่น Button สีต่างๆ และ States ของ Button แต่ละสี เป็นต้น

![Specific component](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variable-specific-component.png)

2. สร้าง Component โดยใช้ Variables กับ Design value ทุกค่า ซึ่งจะไม่มี Raw design value (Hardcode) เกิดขึ้น

![Component](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/component.png)
![Component with variable](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/component-with-variable.png)

## Developer

### Coming soon

## Designer & Developer

### Coming soon
