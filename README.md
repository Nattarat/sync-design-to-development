# RED LAMP - Ways of work between designer and developer

### จุดประสงค์

1. สร้างขั้นตอนการทำงานที่ชัดเจนระหว่าง Designer และ Developer
2. ลดความสับสนและการตัดสินใจที่เกิดจากการทำงานร่วมกันหลายคน หรือการเข้ามาต่องานจากคนที่เริ่มต้นไว้
3. เพิ่มความเร็วของการแก้ไข Theme และการแปลง UI มาเป็น Code

## สารบัญ
* [Designer](#designer)
  - [การเริ่มต้น Design project](#การเริ่มต้น-design-project)
  - [การสร้าง Design systems](#การสร้าง-design-systems)
  - [การแปลง Variables เป็นไฟล์ json เพื่อส่งต่อให้ Developer](#การแปลง-variables-เป็นไฟล์-json-เพื่อส่งต่อให้-developer)
* [Developer](#developer)
  - [การเริ่มต้น Develop project](#การเริ่มต้น-develop-project)
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

2. สร้าง Component โดยใช้ Variables กับ Design value ทุกค่า ซึ่งจะไม่มี Raw design value (Hardcode) เช่น #FFFFFF, 16 เป็นต้น เกิดขึ้น

![Component](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/component.png)
![Component with variable](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/component-with-variables.png)

3. สร้าง Document ของ Color, Typography, Icons และ Assets (Logo, Image)

### การแปลง Variables เป็นไฟล์ json เพื่อส่งต่อให้ Developer
1. ใช้ Figma plugin "Token studio" แปลง Variables เป็นไฟล์ json โดยกด "New empty file"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-1.png)

2. กด "Styles & Variables" > เลือก "Import variables"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-2.png)

3. เลือก "Convert numbers to dimensions" (ถ้าไม่เลือก จะทำให้ Variables ที่ใช้ Alias เกิดการแสดงผลเป็น [object Object]) และ "Use rem to dimensions value"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-3.png)


4. กด "Import all"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-4.png)

5. Collection และ Theme ของ Variables ถูกนำเข้ามาใน Tokens studio

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-5.png)

6. เลือก Theme (Default) ที่ต้องการแปลง Variables เป็นไฟล์ json

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-6.png)

7. กด "Tools" > เลือก "Export to file/folder"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-7.png)


8. ที่ Tab "Single file" ให้นำติ๊กถูกออกจาก "Include parent key" และกด "Export"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-8.png)

9. ตั้งชื่อไฟล์ "variables.json" และกด "Save"

![Token studio](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/tokens-studio-9.png)

## Developer

### การเริ่มต้น Develop project
1. Folder structure ที่ใช้สร้าง UI

```
├── 📄 nuxt.config.ts                    # ใส่ข้อมูล title และ description, ตั้งค่า link (favicon / Embed google font)
├── 📄 tailwind.config.js                # ตั้งค่า Tailwind CSS class เพิ่มเติมจาก Variables เพื่อใช้สร้าง Layout structure (Grid / Flex / Container)
├── 📁 assets
│   ├── 📁 design-systems
│       ├── 📄 _variables.scss           # ที่เก็บ Variables ที่แปลงมาจาก variables.json โดยใช้ Library "style-dictionary"
│       ├── 📄 _specific-variables.scss  # ที่เก็บ Variables ที่มีความเฉพาะในเชิง Development เช่น rem reference, Site container, Z Index, Media query, Transition เป็นต้น
│       ├── 📄 _embed-typography.scss    # ตั้งค่า Font family ที่ไม่มีใน Google font โดยการนำไฟล์ *.ttf, *.otf มา Embed เอง
│       ├── 📄 _typography.scss          # ตั้งค่า Text style ตาม Document ของ Typography ใน Design systems
│       ├── 📄 _mixins.scss              # ที่เก็บ CSS function (Group CSS property)
│       ├── 📄 _scaffolding.scss         # ตั้งค่า CSS property ของ HTML tags
│       ├── 📄 design-systems.scss       # ตั้งค่า Import โดยเรียงลำดับในการเรียกใช้งาน และการ Overwrite style
│       ├── 📄 variables.json            # ไฟล์ json ที่ได้รับมาจาก Designer ซึ่งเก็บ Variables (Object) ไว้ นำไปแปลงเป็น Variables (SCSS) โดยใช้ Library "style-dictionary" ที่ตั้ง Command ไว้ คือ "npm run style"
├── 📁 tailwindcss
│   ├── 📄 tailwindcss.css               # ตั้งค่าใช้งาน Tailwind CSS with Nuxt ตาม [Document](https://tailwindcss.com/docs/guides/nuxtjs)
├── boot
│   └── grub
│       ├── fonts
│       └── locale
├── cdrom
└── dev
    ├── block
    ├── bsg
    └── bus
        └── usb
            ├── 001
            └── 002
```

2. nuxt.config.ts
  - ใส่ข้อมูล "title"
  - ใส่ข้อมูล "description"
  - ใส่ข้อมูล "link" ได้แก่ favicon และ Google font

### Coming soon

## Designer & Developer

### Coming soon
