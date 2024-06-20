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
  - [การสร้าง Component โดยอ้างอิง Variables จาก Design systems](#การสร้าง-component-โดยอ้างอิง-variables-จาก-design-systems)
  - [การตั้งค่า Tailwind CSS class เพิ่มเติมจาก Variables เพื่อใช้สร้าง Layout structure](#การตั้งค่า-tailwind-css-class-เพิ่มเติมจาก-variables-เพื่อใช้สร้าง-layout-structure)
  - [การตั้งค่า Text style (ระดับ Primitive และ Semantic) ตาม Document ของ Typography ใน Design systems](#การตั้งค่า-text-style-(ระดับ-primitive-และ-semantic)-ตาม-document-ของ-typography-ใน-design-systems)
* [Developer & Designer decision](#developer-&-designer-decision)
  - [Scope ของการใช้ Tailwind CSS class และ Local (Page) style](#scope-ของการใช้-tailwind-css-class-และ-local-(page)-style)

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
📁 project
├── 📄 nuxt.config.ts                    # ใส่ข้อมูล title และ description, ตั้งค่า link (favicon / Embed google font) และเรียกใช้ Vue library
├── 📄 tailwind.config.js                # ตั้งค่า Tailwind CSS class เพิ่มเติมจาก Variables เพื่อใช้สร้าง Layout structure (Grid / Flex / Container)
├── 📁 assets
│   ├── 📁 design-systems
│   │   ├── 📄 _variables.scss           # ที่เก็บ Variables ที่แปลงมาจาก variables.json โดยใช้ Library "style-dictionary"
│   │   ├── 📄 _specific-variables.scss  # ที่เก็บ Variables ที่มีความเฉพาะในเชิง Development เช่น rem reference, Site container, Z Index, Media query, Transition เป็นต้น
│   │   ├── 📄 _embed-typography.scss    # ตั้งค่า Font family ที่ไม่มีใน Google font โดยการนำไฟล์ *.ttf หรือ *.otf มา Embed เอง
│   │   ├── 📄 _typography.scss          # ตั้งค่า Primitive text style ตาม Document ของ Typography ใน Design systems
│   │   ├── 📄 _mixins.scss              # ที่เก็บ CSS function (Group CSS property)
│   │   ├── 📄 _scaffolding.scss         # ตั้งค่า CSS property ของ HTML tags
│   │   ├── 📄 design-systems.scss       # ตั้งค่า Import โดยเรียงลำดับในการเรียกใช้งาน และการ Overwrite style
│   │   └── 📄 variables.json            # ไฟล์ json ที่ได้รับมาจาก Designer ซึ่งเก็บ Variables (Object) ไว้ นำไปแปลงเป็น Variables (SCSS) โดยใช้ Library "style-dictionary" ที่ตั้ง Command ไว้ คือ "npm run style"
├── ├── 📁 tailwindcss
│   │   └── 📄 tailwindcss.css           # ตั้งค่าใช้งาน Tailwind CSS with Nuxt ตาม https://tailwindcss.com/docs/guides/nuxtjs
├── └── 📄 style-global.scss             # ที่เก็บ Class ของ Semantic text style (Display / Title / Label / Body) และ Utility classes ที่ใช้งานทั่วไป (* แนะนำว่าถ้าไม่จำเป็นไม่ควรมาสร้างไว้ เพราะ Tailwind CSS มี Support ไว้หมดแล้ว)
├── 📁 components
│   ├── 📁 Button
│   │   └── 📄 Button.vue                # ไฟล์ Vue component โดย Structure แบ่งเป็น 3 ส่วน คือ Template (HTML), Script (JS) และ Style (SCSS)
├── └── 📄 components.ts                 # ตั้งค่า Import Vue component ไปใช้งาน
├── 📁 layouts
├── └── 📄 default.vue                   # ไฟล์ Vue component ที่ทำหน้าที่เป็น Layout ของ Page
├── 📁 pages
├── └── 📄 index.vue                     # ไฟล์ Vue component ที่ทำหน้าที่เป็น Page โดยมีการเรียกใช้ Layout ตามที่กำหนดไว้
├── 📁 plugins
├── └── 📄 vue-notification.ts           # ตั้งค่า Import Vue library ไปใช้งาน
└── 📁 plublic
    ├── 📁 favicons                      # ที่เก็บไฟล์รูป favicon
    ├── 📁 fonts                         # ที่เก็บไฟล์ Font family (*.ttf หรือ *.otf) ที่ไม่มีใน Google font
    ├── 📁 images
    │   ├── 📁 contents                  # ที่เก็บไฟล์รูป Mockup ของ Content ที่ต้องดึงจาก API มาแสดง เช่น Profile image, Product เป็นต้น
    ├── 📁 graphics                      # ที่เก็บไฟล์รูป Decoration ของ Design เช่น Pattern, Illustration เป็นต้น
    ├── 📁 icons                         # ที่เก็บไฟล์รูป Icon (แนะนำ Export เป็น svg และ png เพื่อให้สามารถดู Preview แบบ Thumbnail ได้)
    ├── 📁 logos                         # ที่เก็บไฟล์รูป Logo (แนะนำ Export เป็น svg และ png เพื่อให้สามารถดู Preview แบบ Thumbnail ได้)
    ├── 📁 placeholder                   # ที่เก็บไฟล์รูป Placeholder (รูปที่ใช้แทนกรณียังไม่มีข้อมูล)
    └── 📄 manifest.json                 # ตั้งค่า Icon, Title, Description บนหน้า Home Screen เมื่อผู้ใช้งาน Mobile กดปุ่ม Add to home Screen และกำหนดให้เว็บไซต์เป็นแบบ Full screen mode ไม่มี Address bar ซึ่งจะทำให้การแสดงผลมีความใกล้เคียงกับแอปพลิเคชั่น ควบคุมมุมมองแนวตั้ง แนวนอนของเว็บได้ กำหนดสีและ Splash screen ได้
```
2. การนำ variables.json มาแปลงเป็น SCSS variables

### การสร้าง Component โดยอ้างอิง Variables จาก Design systems
1. นำ variables.json ที่ได้รับมาจาก Designer มาวางไว้ที่ ./assets/design-systems (วางแบบ Replace ได้เลย)
2. เปิด Terminal และใส่ Command "npm run style" เพื่อแปลง variables.json เป็น _variables.scss เพื่อให้ได้ Variables ไปใช้งานในการเขียน CSS

![Command style dictionary](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/command-style-dictionary.png)
![variables](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/variables.png)

3. เขียน CSS ของ Component โดยใช้ Variable ที่กำหนดไว้ใน Design systems
* เข้า Figma link ของ Design systems ที่ได้รับมาจาก Designer (รูปภาพ Component ตัวอย่าง คือ Button)

![View component](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/component-view.png)

* มาที่ Component variants และดู Variant properties ทั้งหมด เพื่อวางแผนการเขียน CSS class

![Component variants](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/component-variants.png)

* CSS structure แบ่งออกเป็น 4 ส่วน คือ Parent style, Children style, Modifier style และ Other component style
  - Parent style   : CSS ของ HTML ที่เป็น Component main container
  - Children style : CSS class ของ HTML ที่อยู่ภายใน Component main container
  - Modifier style : CSS class เสริมของ Component main container เขียนเพื่อ Overwrite CSS ของ Component main container และ CSS class ของ HTML ที่อยู่ภายใน Component main container ตัวอย่างเช่น &.color-small {...} ที่ใช้เปลี่ยนขนาด, &.color-red {...} ที่ใช้เปลี่ยนสี เป็นต้น
  - Other component style : CSS class ของ Component อื่น ที่ถูกนำมาอยู่ภายใน Component main container

![CSS strusture](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/css-structure.png)

* ที่ Parent style เขียน CSS ให้เกิด Transition เมื่อเปลี่ยน State ของ Button

![CSS parent style](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/css-parent-style.png)

* ที่ Children style เขียน CSS class ของ Container text เพื่อสร้างระยะห่างของ Front/Back icon กับ Text
  - ดู variables ที่ถูกใช้กับ Container text ของ Button และทำการ Copy ค่า Variables ของ Layout มาใช้

  ![Inspect variable button text](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/inspect-variable-button-text.png)

  - Paste ค่า Variables ของ Layout

  ![Copy paste variable button text](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/copy-paste-variable-button-text.png)

  - ลบ CSS properties ที่ไม่ใช้ออกไป

  ![Delete unused css properties button text](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/delete-unused-css-properties-button-text.png)

  - นำ Variables มาใช้งาน โดยทำตามขั้นตอน ดังนี้ [1] Cut variable name [2] ลบ Var(--) [3] พิมพ์ $ [4] Paste variable name [5] กด Ctrl + Spacebar [6] เลือก Variable ที่แนะนำขึ้นมาให้ตรงกับ Variable name [7] ลบ Dollar sign ที่เกินมาออก [กดดู Video แสดงขั้นตอนตามลำดับที่นี่](https://drive.google.com/file/d/1s6WNy88OMn6jb6juE0LnixtqNVTu7CRQ/view?usp=drive_link)

  ![Finished add variable button text](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/finished-add-variable-button-text.png)

* ที่ Modifier style
  - เขียน CSS class ขนาด Medium ของ Button

  ![CSS parent style](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/css-modifier-style-blank.png)

  - ดู variables ที่ถูกใช้กับ Container ของ Button ขนาด Medium และทำการ Copy ค่า Variables ของ Layout มาใช้

  ![Inspect variable button size](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/inspect-variable-button-size.png)

  - Paste ค่า Variables ของ Layout

  ![Copy paste variable button size](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/copy-paste-variable-button-size.png)

  - ลบ CSS properties ที่ไม่ใช้ออกไป

  ![Delete unused css properties button size](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/delete-unused-css-properties-button-size.png)

  - นำ Variables มาใช้งาน โดยทำตามขั้นตอน ดังนี้ [1] Cut variable name [2] ลบ Var(--) [3] พิมพ์ $ [4] Paste variable name [5] กด Ctrl + Spacebar [6] เลือก Variable ที่แนะนำขึ้นมาให้ตรงกับ Variable name [7] ลบ Dollar sign ที่เกินมาออก [กดดู Video แสดงขั้นตอนตามลำดับที่นี่](https://drive.google.com/file/d/1qiUDOhcQ8_9tokl0rDuZywoKCkZkD0IE/view?usp=drive_link)

  - ดู variables ที่ถูกใช้กับ Container ของ Button ขนาด Medium และทำการ Copy ค่า Variables ของ Text มาใช้

  ![Inspect variable button size text](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/inspect-variable-button-size-text.png)

  - Paste ค่า Variables ของ Text

  ![Copy paste variable button size text](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/copy-paste-variable-button-size-text.png)

  - ลบ CSS properties ที่ไม่ใช้ออกไป

  ![Delete unused css properties button size](https://raw.githubusercontent.com/Nattarat/sync-design-to-development/main/images/delete-unused-css-properties-button-size-text.png)

  - นำ Variables มาใช้งาน โดยทำตามขั้นตอน ดังนี้ [1] Cut variable name [2] ลบ Var(--) [3] พิมพ์ $ [4] Paste variable name [5] กด Ctrl + Spacebar [6] เลือก Variable ที่แนะนำขึ้นมาให้ตรงกับ Variable name [7] ลบ Dollar sign ที่เกินมาออก [กดดู Video แสดงขั้นตอนตามลำดับที่นี่](https://drive.google.com/file/d/1bi8EbNyShhszfNHvUiCRNRr_osrEjmJE/view?usp=drive_link)

  - ในกรณีตั้งค่า Text style (ระดับ Primitive และ Semantic) ตาม Document ของ Typography ใน Design systems เรียบร้อยแล้ว สามารถข้ามขั้นตอนการนำ Variables มาใช้งานตรงๆ ได้เลย โดยการใช้ mixins แทน ซึ่งทำตามขั้นตอน ดังนี้ [1] หลังจาก Copy & Paste ค่า Variables ของ Text มาแล้วให้ลบ CSS properties ออก [2] Copy Text style name ที่เป็น Comment และมีลักษณะ "semantic/body/md-leading-none" [3] พิมพ์ @include [4] Paste text style name [5] กด Ctrl + Spacebar [6] เลือก Mixins ที่แนะนำขึ้นมาให้ตรงกับ Text style name [7] ลบ Text ที่อยู่ด้านของ typography/... ออก [กดดู Video แสดงขั้นตอนตามลำดับที่นี่](https://drive.google.com/file/d/1HAP61CANxI5SX_kIFopzlPNQ9kRb8eMl/view?usp=drive_link)

### การตั้งค่า Tailwind CSS class เพิ่มเติมจาก Variables เพื่อใช้สร้าง Layout structure
* Coming soon

### การตั้งค่า Text style (ระดับ Primitive และ Semantic) ตาม Document ของ Typography ใน Design systems
* Coming soon

## Developer & Designer decision

### Scope ของการใช้ Tailwind CSS class และ Local (Page) style
* Coming soon
  - แบ่งการใช้งาน Grid และ Flex ให้ชัดเจน
  - ควรใช้ div เปล่าๆ เพื่อบ่งบอกว่าเป็น Layout structure (Row, Column) หรือไม่ เพราะ การนำ Content มาวางโดยตรงจะโดน Children style ของ Parent (Grid / Flex) กระทบได้ นอกจากนี้ การ Overwrite style โดยไม่ตั้งใจของ Content อาจจะกระทบ Children style ของ Parent (Grid / Flex) ได้ด้วยเช่นกัน [Tradeoff คือ Nesting html เยอะขึ้น แต่ก็ทำให้สังเกต Layout structure (Row, Column) ได้ง่ายขึ้นตอบแทนกลับมา]
  - Local (Page) style ควรใช้กับ Reuse UI ไม่เช่นนั้นเวลาแก้ไขต้องไปไล่แก้ที่ Tailwind CSS class ทุกที่
