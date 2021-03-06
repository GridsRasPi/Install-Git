# Install-Git
 ติดตั้งใช้งาน Git
 
### Install Git-scm

~~~
$ sudo apt-get install git
~~~

### Gid Command

**กำหนดค่าผู้ใช้งาน**

_คำสั่ง CLI_

ก่อนจะไปใช้คำสั่ง git เรามาร้จักคำสั่ง CLI กันก่อน

- **pwd** (print working directory (dir)) ใช้เมื่ออยากรู้ว่าตอนนี้เราอยู่ที่ dir ไหน
- **cd** (change dir) เพื่อเปลี่ยนไปยัง dir อื่น
- **ls** (list) ดูว่าใน dir ที่เราอยู่มีไฟล์หรือโฟลเดอร์อะไรบ้าง
- **mkdir** (make dir) สร้างโฟลเดอร์ใหม่ขึ้นมา
- **touch** สร้างไฟล์ใหม่

_คำส่ัง git_

โดยพื้นฐานแล้ว git มีคำสั่งที่หลากหลาย เริ่มกันด้วยคำสั่งเบื้องต้น

- **git init** ใช้สร้าง local repo ขึ้นมา
- **git add** ใช้ stage เพื่อติดตามตามความเปลี่ยนแปลงของไฟล์
- **git commit** ใช้เพื่อบันทึกความเปลี่ยนแปลงที่เกิดขึ้นสู่ local repo
- **git push** ใช้เพื่อส่ง commit ไปยัง remote repo
- **git clone** ใช้เพื่อคัดลอก repo จาก remote มายัง local
- **git fetch** ใช้ดึงความเปลี่ยนแปลงจาก remote มายัง local แต่ยังไม่รวมเข้าด้วยกัน
- **git merge** ใช้รวมความเปลี่ยนแปลงที่ได้มาจาก fetch เข้ากับ local
- **git pull** ใช้ดึงความเปลี่ยนแปลงจาก remote มายัง local และรวมเข้าด้วยกัน (มีค่าเท่ากับ fetch+merge)
- **git log** ใช้เพื่อดูว่า git repo มี commit อะไรแล้วบ้าง

~~~
git config ต่อด้วย Option
~~~

ใช้สำหรับ การเปลี่ยนแปลง และ การกำหนดค่าผู้ใช้เริ่มต้นของ Git

**_NOTE_** : เราสามารถเพิ่ม -global เพื่อให้ทุกๆ repo สามารถใช้ config เดียวกันนี้ได้

**_NOTE_** : จากตัวอย่างเวลานำไปใช้งานจริงไม่ต้องใส่สัญลักษณ์นี้ "[ ]" 

~~~
git config -–global user.name "[user name]" 
~~~

ใช้ในการเซต username ที่จะแสดงบน origin

~~~
git config -–global user.email "[email address]" 
~~~

ใช้ในการเซต email ผู้ใช้

~~~
git config --global user.password "your password" 
~~~

ใช้ในการเซต password ผู้ใช้งาน

**_หมายเหตุ_** ในกรณีที่เราใช้ git เป็น SSH ไม่จำเป็น set password

**กำหนดค่าโครงการ**

~~~
git init
~~~

ใช้ในการ “intialize” โครงการ หรือ ก็คือการกำหนดค่าเริ่มต้นให้กับโครงการของเราก่อนที่เราจะเริ่มใช้งาน git 

~~~
git clone  ต่อด้วย URL
~~~

**ตัวอย่าง**

~~~
git clone https://github.com/GridsRasPi/Project-XXXX.git
~~~

ใช้สำหรับ clone repositories ลงมาจาก Web เพื่อทำงานต่อ (ใช้กรณีที่ไม่เคยมี Repository นี้มาก่อน)

~~~
git status
~~~

status คือ การตรวจสอบสถานะของแฟ้ม ถ้ามีการเปลี่ยนแปลงก็จะแสดงให้เราเห็นว่ามีการแก้ที่ไหน ก่อนที่เราจะทำการใช้ git add ลำดับถัดไป

~~~
git add
~~~

add คือ การเพิ่มไฟล์ที่มีการเปลี่ยนแปลงก่อนเพื่อจะ commit โดยแบ่งตามการทำงานดังนี้

~~~
git add . 
~~~

หมายถึง ต้องการเพิ่มไฟล์ทั้งหมดที่มีการเปลี่ยนแปลงก่อนจะ commit

~~~
git add [path] 
~~~

หมายถึง ต้องการแอดทีละไฟล์ ตามพาธที่เราต้องการ (unstage -> stage) ก่อนจะ commit

git commit

commit คือ เริ่มเก็บประวัติการเปลี่ยนแปลงของแฟ้มต่างๆ ก่อนที่จะ ในโปรเจคโดยตอนนี้จะยังอยู่ใน Local Repository ส่วน -a หมายถึง All คือทั้งหมดที่มีการเปลี่ยนแปลง ส่วน -am ทั้งหมดและต้องการใส่คอมเม้นข้อความด้วย

git push origin [branch name]
push คือ การส่ง commit ที่ Local Repository ไปยัง Remote Repository

git pull origin [branch name]
pull คือ การดึง Remote Repository ไฟล์มายัง Local Repository เพื่อทำการอัพเดต โดยหลักๆที่จะเจอคือ pull มาแล้วทำงานต่อได้เลยและอีกแบบ pull มาแล้วเกิดการ merge และอาจจะเกิด conflict file กันซึ่งเราก็ต้องทำการแก้ไฟล์ที่ error แจ้งมาจะบอกว่าไฟล์อะไรบ้างที่มีการ conflict



Exit Repo

**Action ในการทำงาน**

git add . 

คือถ้าต้องการเพิ่ม ไฟน์ทั้งหมดที่มีการเปลี่ยนแปลง ก่อนจะ commit

git add [path] 

คือถ้าต้องการเพิ่ม เฉพาะไฟน์ที่มีการเปลี่ยนแปลให้กำหนดเส้นทางหรือ path ก่อนจะ commit

git commit

commit เป็นกล่องสำหรับเก็บข้อมูลประวัติการทำงานที่ส่งมาโดย add แต่ยังไม่มีการส่งขึ้นไปยัง Server

**_หมายเหตุ_** : 
- -a หมายถึง All คือจัดเก็บทั้งหมดที่มีการเปลี่ยนแปลง
- -am คือจัดเก็บทั้งหมดที่มีการเปลี่ยนแปลง เหมือน -a และ มีคอมเม้นด้วยโดยการคอมเม้นต้องมีเครื่องหมาย ' ' ค่อมข้อความที่เราต้องการแนบไปด้วย

Push

pull



