# การทดลอง พื้นฐาน JavaScript และการใช้งานร่วมกับ HTML/CSS
## การทดลองที่ 1 : ทำความรู้จักกับ JavaScript
###  การเพิ่ม JavaScript ลงในเว็บเพจ

JavaScript สามารถเพิ่มลงในเว็บเพจได้ 3 วิธี:

1. แบบ Inline: แทรก scipt ในแต่ละบรรทัดของ HTML Element
```html
<button onclick="alert('สวัสดี!')">คลิกที่นี่</button>
```

2. แบบ Internal Script: เขียน script ใน block   <script> </script>
```html
<script>
    alert('สวัสดี!');
</script>
```

3. แบบ External Script: เขียน script ในไฟล์แล้วเรียกใช้ใน HTML
   ไฟล์ script.js มีข้อมูลดังนี้
```javascript
    alert('สวัสดี!');
```
   ไฟล์ HTML มีการเรียกใช้ script ดังนี้
```html
<script src="script.js"></script>
```

### การทดลองที่ 1.1 : สร้างไฟล์ HTML และทดลองใช้ JavaScript ทั้ง 3 แบบ

สร้างไฟล์ `index.html`:
```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <title>ทดลอง JavaScript</title>
</head>
<body>
    <!-- Inline JavaScript -->
    <button onclick="alert('คลิกปุ่มที่ 1!')">ปุ่มที่ 1</button>

    <!-- ทดสอบ Internal JavaScript -->
    <button id="btn2">ปุ่มที่ 2</button>

    <!-- ทดสอบ External JavaScript -->
    <button id="btn3" onclick="hello3();">ปุ่มที่ 3</button>

    <!-- Internal JavaScript -->
    <script>
        document.getElementById('btn2').onclick = function() {
            alert('คลิกปุ่มที่ 2!');
        };
    </script>

    <!-- External JavaScript -->
    <script src="script.js"></script>
</body>
</html>
```

### แบบฝึกปฏิบัติที่ 1: การใช้งาน JavaScript เบื้องต้น

1. สร้างหน้าเว็บที่มีปุ่ม 3 ปุ่ม:
   - ปุ่มที่ 1: ใช้ Inline JavaScript แสดงชื่อนักศึกษา
   - ปุ่มที่ 2: ใช้ Internal JavaScript แสดงวันที่ปัจจุบัน
   - ปุ่มที่ 3: ใช้ External JavaScript แสดงเวลาปัจจุบัน

2. เพิ่มกล่องข้อความและปุ่มสำหรับแสดงผล:
   - มีช่องกรอกข้อความ
   - มีปุ่มเมื่อคลิกแล้วจะแสดงข้อความที่กรอกในช่องข้อความ
### บันทึกผลการทดลอง 
โค้ด html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- Inline JavaScript -->
    <button onclick="alert('theeranat phutiwanich')">แสดงชื่อนักศึกษา</button>

    <!-- ทดสอบ Internal JavaScript -->
    <button id="btn2">แสดงวันที่ปัจจุบัน</button>

    <!-- ทดสอบ External JavaScript -->
    <button id="btn3" onclick="hello3();">แสดงเวลาปัจจุบัน</button>

    <!-- Internal JavaScript -->
    <script>
        document.getElementById('btn2').onclick = function() {
            alert('Tuesday, February 11, 2025');
        };
    </script>

    <form id="info">
        <div class="name">
            <p>fullname</p>
            <label for="fullname">Name :</label>
            <input type="text" name="fullname" id="fullname" required>
        </div>
        <button id="fullname" onclick="hello4()">show fullname</button>
    </form>

    <!-- External JavaScript -->
    <script src="script.js"></script>
</body>
</html>
```
โค้ด js
```js
document.getElementById('btn3').onclick = function() {
    alert('3:28 PM');
};

function hello4() {
    const fullname = document.getElementById('fullname').value;
    if (fullname) {
        alert(`Full Name: ${fullname}`);
    } else {
        alert('Please enter your full name.');
    }
}

document.getElementById('show-fullname-btn').addEventListener('click', hello4);
```
[รูปผลการทดลองที่ 1]
![image](https://github.com/user-attachments/assets/bd4a7470-6410-4ff5-bd9b-1c3c8d46f38e)
![image](https://github.com/user-attachments/assets/2db71edd-4b9f-4aa9-9ccc-e5f5703c4d61)
![image](https://github.com/user-attachments/assets/48bfbaa8-e4cb-45b2-86da-342ff0a0a154)
![image](https://github.com/user-attachments/assets/c8a561d7-b54c-4b05-b0dc-44d3c7c63f3d)

## การทดลองที่ 2: พื้นฐาน JavaScript
### 2.1 การประกาศตัวแปรและชนิดข้อมูล

JavaScript มีวิธีการประกาศตัวแปร 3 แบบ:
- `var`: ประกาศตัวแปรแบบเดิม (legacy) - ไม่แนะนำให้ใช้ในโค้ดสมัยใหม่
- `let`: ประกาศตัวแปรที่สามารถเปลี่ยนแปลงค่าได้ - เหมาะสำหรับค่าที่ต้องการเปลี่ยนแปลงในภายหลัง
- `const`: ประกาศตัวแปรที่ไม่สามารถเปลี่ยนแปลงค่าได้ - เหมาะสำหรับค่าคงที่

ชนิดข้อมูลพื้นฐานใน JavaScript:
1. Number: ตัวเลขทั้งจำนวนเต็มและทศนิยม
2. String: ข้อความ ใช้เครื่องหมาย '' หรือ ""
3. Boolean: ค่าความจริง true/false
4. Undefined: ตัวแปรที่ยังไม่ได้กำหนดค่า
5. Null: ตัวแปรที่ไม่มีค่า (ต่างจาก undefined)
6. Array
7. Object
   
### ตัวอย่าง การประกาศตัวแปรแต่ละแบบ
```javascript
// ประกาศตัวแปรแบบ let - สามารถเปลี่ยนแปลงค่าได้ในภายหลัง
let name = "สมชาย";     // String เก็บข้อความ
let age = 25;           // Number เก็บตัวเลข
let isStudent = true;   // Boolean เก็บค่าจริง/เท็จ

// ประกาศตัวแปรแบบ const - ไม่สามารถเปลี่ยนแปลงค่าได้หลังจากประกาศ
const PI = 3.14;            // ค่าคงที่ทางคณิตศาสตร์
const DAYS_IN_WEEK = 7;     // ค่าคงที่ที่ไม่ควรเปลี่ยนแปลง

// การเปลี่ยนแปลงค่าตัวแปร
name = "สมหญิง";   // ทำได้เพราะประกาศด้วย let
age = 26;          // สามารถเปลี่ยนค่าได้
// PI = 3.15;      // Error! ไม่สามารถเปลี่ยนค่า const ได้

// ตัวอย่างการใช้งาน undefined และ null
let uninitializedVar;           // มีค่าเป็น undefined โดยอัตโนมัติ
let emptyValue = null;          // กำหนดค่า null อย่างชัดเจน

// ตัวอย่างการประกาศ Array
let fruits = ["แอปเปิ้ล", "กล้วย", "ส้ม"];

// ตัวอย่างการประกาศ Object
let person = {
    name: "สมชาย",
    age: 25,
    isStudent: true
};
```

### 📝 แบบทดสอบที่ 2.1: การทดลองประกาศตัวแปร
1. สร้างตัวแปรเก็บข้อมูล รหัสนักศึกษา ชื่อนักศึกษา คะแนนสอบกลางภาค, คะแนนสอบปลายภาค โดยเลือกใช้ let หรือ const 
2. สร้าง Object สำหรับเก็บข้อมูลนักศึกษา  ประกอบด้วยข้อมูล รหัสนักศึกษา, ชื่อ, สาขาวิชา, เกรดเฉลี่ย

### บันทึกผลการทดลอง 2.1
```js
const ID = "67030098";
const nameSD = "Theeranat Phutiwanich"
const midtermScores = 70;

const personSD = {
    ID: "67030098",
    nameSD: "Theeranat Phutiwanich",
    branch: "Computer Technology",
    gpa: 37.00,
};

console.log(ID);
console.log(nameSD);
console.log(midtermScores);
console.log(personSD)
```
[รูปผลการทดลองที่ 2.1]

![image](https://github.com/user-attachments/assets/9e318523-cd8e-46a8-b870-a404b0b10e84)

### 2.2 การดำเนินการทางคณิตศาสตร์

JavaScript มีตัวดำเนินการทางคณิตศาสตร์พื้นฐานดังนี้:
- `+` การบวก
- `-` การลบ
- `*` การคูณ
- `/` การหาร
- `%` การหารเอาเศษ (modulo)
- `**` การยกกำลัง (exponentiation)
- `++` การเพิ่มค่าทีละ 1 (increment)
- `--` การลดค่าทีละ 1 (decrement)

### แบบฝึกหัด 2.2: ทดลองใช้ตัวดำเนินการทางคณิตศาสตร์
```javascript
// กำหนดค่าตัวแปรเริ่มต้น
let x = 10;
let y = 5;

// การดำเนินการพื้นฐาน
let sum = x + y;      // บวก: 10 + 5 = 15
let diff = x - y;     // ลบ: 10 - 5 = 5
let product = x * y;  // คูณ: 10 * 5 = 50
let quotient = x / y; // หาร: 10 / 5 = 2
let remainder = x % y; // หารเอาเศษ: 10 % 5 = 0 (หาร 5 ลงตัว)

// การเพิ่ม/ลดค่าทีละ 1
let counter = 1;
counter++;            // เพิ่มค่าทีละ 1: counter = 2
counter--;            // ลดค่าทีละ 1: counter = 1

// การยกกำลัง
let squared = x ** 2;  // 10 ยกกำลัง 2 = 100
let cubed = x ** 3;    // 10 ยกกำลัง 3 = 1000

// การใช้ตัวดำเนินการร่วมกับการกำหนดค่า
let number = 5;
number += 3;          // เท่ากับ number = number + 3
number -= 2;          // เท่ากับ number = number - 2
number *= 4;          // เท่ากับ number = number * 4
number /= 2;          // เท่ากับ number = number / 2

```

### 📝 แบบทดสอบที่ 2.2: การคำนวณพื้นฐาน
1. เขียนโปรแกรม กำหนดคะแนน  3 วิชา แล้วหาค่าคะแนนเฉลี่ย แล้วแสดงผลการคำนวณ
2. เขียนโปรแกรม กำหนดชื่อสินค้า ราคาสินค้า คำนวณราคาสินค้าที่รวม VAT 7% แล้วแสดงผลการคำนวณ

### บันทึกผลการทดลอง 2.2
```js
let math = 70;
let thai = 90;
let eng = 85;

let sum = math + thai + eng;
let result = sum / 3;

console.log("score : ", result);
```
```js
const nameProduct = "Mobile";
const priceProduct = 85;
const VAT = .07;
const maxprice = priceProduct + (priceProduct * VAT);

console.log("maxprice : ", maxprice);
```
[รูปผลการทดลองที่ 2.2]
![image](https://github.com/user-attachments/assets/3f40b240-9f6f-42ab-ac96-d400873b2d9f)

### 2.3 การควบคุมการทำงาน

JavaScript มีโครงสร้างควบคุมการทำงานหลักๆ ดังนี้:

1. เงื่อนไข (Conditionals):
   - `if`: ตรวจสอบเงื่อนไขเดียว
   - `if...else`: ตรวจสอบเงื่อนไขและมีทางเลือก
   - `if...else if...else`: ตรวจสอบหลายเงื่อนไข
   - `switch`: เลือกทำงานตามค่าที่กำหนด

2. การวนซ้ำ (Loops):
   - `for`: วนซ้ำตามจำนวนรอบที่กำหนด
   - `while`: วนซ้ำตราบใดที่เงื่อนไขเป็นจริง
   - `do...while`: ทำงานอย่างน้อย 1 ครั้ง แล้ววนซ้ำตามเงื่อนไข
   - `for...of`: วนซ้ำสำหรับข้อมูลแบบ iterable
   - `for...in`: วนซ้ำสำหรับ properties ใน object


```javascript
// 1. การใช้ if-else
let score = 75;

// ตรวจสอบเงื่อนไขตามลำดับ
if (score >= 80) {         // ถ้าคะแนน >= 80
    console.log("เกรด A");
} else if (score >= 70) {  // ถ้าคะแนน >= 70 แต่ < 80
    console.log("เกรด B");
} else {                   // ถ้าไม่ตรงเงื่อนไขใดเลย
    console.log("เกรด C");
}

// 2. การใช้ switch
let day = 1;
switch (day) {
    case 1:
        console.log("วันจันทร์");
        break;              // break เพื่อออกจาก switch
    case 2:
        console.log("วันอังคาร");
        break;
    default:               // ค่าเริ่มต้นถ้าไม่ตรงกับ case ใดๆ
        console.log("วันอื่นๆ");
}

// 3. การใช้ for loop
// วนซ้ำ 5 รอบ: เริ่มที่ 1, ทำจนถึง 5, เพิ่มค่าทีละ 1
for (let i = 1; i <= 5; i++) {
    console.log("รอบที่", i);
}

// 4. การใช้ while loop
// วนซ้ำตราบใดที่เงื่อนไขเป็นจริง
let count = 1;
while (count <= 3) {      // ทำซ้ำตราบใดที่ count <= 3
    console.log("นับ:", count);
    count++;              // เพิ่มค่า count ทีละ 1
}

// 5. การใช้ do...while loop
// ทำงานอย่างน้อย 1 ครั้ง แล้วค่อยตรวจสอบเงื่อนไข
let num = 1;
do {
    console.log("ตัวเลข:", num);
    num++;
} while (num <= 3);

// 6. การใช้ for...of loop กับ array
let fruits = ['แอปเปิ้ล', 'กล้วย', 'ส้ม'];
for (let fruit of fruits) {
    console.log("ผลไม้:", fruit);
}

// 7. การใช้ for...in loop กับ object
let person = {
    name: 'สมชาย',
    age: 25,
    job: 'โปรแกรมเมอร์'
};
for (let key in person) {
    console.log(key + ":", person[key]);
}

// 8. การใช้เงื่อนไขซ้อน (Nested Conditions)
let age = 18;
let hasPermission = true;

if (age >= 18) {
    if (hasPermission) {
        console.log("สามารถเข้าใช้งานได้");
    } else {
        console.log("ต้องได้รับอนุญาตก่อน");
    }
} else {
    console.log("อายุไม่ถึงเกณฑ์");
}

// 9. การใช้ตัวดำเนินการลอจิคัล (Logical Operators)
let isStudent = true;
let isMember = false;

if (isStudent && isMember) {           // AND (&&)
    console.log("เป็นทั้งนักเรียนและสมาชิก");
} else if (isStudent || isMember) {    // OR (||)
    console.log("เป็นอย่างใดอย่างหนึ่ง");
} else {
    console.log("ไม่เป็นทั้งสองอย่าง");
}

// 10. การใช้ break และ continue
for (let i = 1; i <= 5; i++) {
    if (i === 3) {
        continue;    // ข้ามการทำงานที่เหลือในรอบนี้
    }
    if (i === 4) {
        break;       // ออกจาก loop ทันที
    }
    console.log("ตัวเลข:", i);
}
```


### 📝 แบบทดสอบที่ 2.3: การควบคุมการทำงาน
1. กำหนดตัวเลข และตรวจสอบว่าตัวเลขที่กำหนดเป็นเลขคู่หรือเลขคี่
2. สร้าง loop แบบ for แสดงตารางสูตรคูณ แม่ 2 และ loop แบบ while แสดงสูตรคูณ แม่ 3
3. เขียนโปรแกรมนับถอยหลังจาก 10 ถึง 1
4. เขียนโปรแกรมกำหนดอายุ และตรวจสอบช่วงวัยตามอายุที่กำหนด (กำหนดอายุแต่ละช่วงวัย วัยเด็ก วัยรุ่น วัยผู้ใหญ่)

### บันทึกผลการทดลอง 2.3
```js
let number = 4;

if (number % 2 === 0) {
    console.log('เป็นเลขคู่');
} else {
    console.log('เป็นเลขคี่');
}
```
```js
for (let i = 1; i <= 12; i++) {
    console.log(`2 x ${i} = ${2 * i}`);
}
```
```js
let j = 1;
while (j <= 12) {
    console.log(`3 x ${j} = ${3 * j}`);
    j++;
}
```
```js
for (let k = 10; k >= 1; k--) {
    console.log(k);
}
```
```js
let age = 23;
if (age < 0) {
} else if (age <= 12) {
    console.log(`อายุ ${age}: วัยเด็ก`);
} else if (age <= 19) {
    console.log(`อายุ ${age}: วัยรุ่น`);
} else if (age <= 59) {
    console.log(`อายุ ${age}: วัยผู้ใหญ่`);
} else {
    console.log(`อายุ ${age}: วัยสูงอายุ`);
}
```
[รูปผลการทดลองที่ 2.3]

![image](https://github.com/user-attachments/assets/ea22e90b-989b-43a0-b203-5ba6cfc9965e)

### 2.4 Functions และ Arrow Functions

Functions คือกลุ่มคำสั่งที่สามารถนำมาใช้ซ้ำได้ ใน JavaScript มีวิธีการเขียน function 2 แบบหลักๆ:

1. Function แบบปกติ (Regular Functions):
   - ใช้คำสั่ง `function` ในการประกาศ
   - สามารถมีหรือไม่มีพารามิเตอร์ก็ได้
   - สามารถ return ค่ากลับหรือไม่ก็ได้
   - มี `this` context ของตัวเอง

2. Arrow Functions:
   - เป็นวิธีเขียนแบบสั้นที่มาใน ES6
   - ไม่มี `this` context ของตัวเอง
   - เหมาะสำหรับ function สั้นๆ
   - มักใช้ใน callback functions

#### ตัวอย่างการสร้างและเรียกใช้ Function 

```javascript
// 1. Function พื้นฐาน - ไม่มีพารามิเตอร์และไม่ return ค่า
function sayHello() {
    console.log("สวัสดี!");
}
sayHello();  // เรียกใช้ function: แสดง "สวัสดี!"

// 2. Function ที่รับพารามิเตอร์
function greet(name) {
    console.log("สวัสดี " + name);
}
greet("สมชาย");  // แสดง: "สวัสดี สมชาย"

// 3. Function ที่ return ค่า
function add(a, b) {
    return a + b;  // ส่งค่าผลบวกกลับ
}
let sum = add(5, 3);  // sum = 8

// 4. Function ที่มีค่าเริ่มต้นของพารามิเตอร์
function greetWithTitle(name, title = "คุณ") {
    console.log("สวัสดี " + title + " " + name);
}
greetWithTitle("สมชาย");          // แสดง: "สวัสดี คุณ สมชาย"
greetWithTitle("สมชาย", "ดร.");   // แสดง: "สวัสดี ดร. สมชาย"

// 5. Function ที่รับหลายพารามิเตอร์ (Rest Parameters)
function sum(...numbers) {
    let total = 0;
    for (let num of numbers) {
        total += num;
    }
    return total;
}
console.log(sum(1, 2, 3, 4));  // แสดง: 10

// 6. Function ที่ return หลายค่าโดยใช้ Object
function getPersonInfo() {
    return {
        name: "สมชาย",
        age: 25,
        job: "โปรแกรมเมอร์"
    };
}
let person = getPersonInfo();
console.log(person.name);  // แสดง: "สมชาย"

// 7. Function ที่เป็น Method ใน Object
let calculator = {
    add: function(a, b) {
        return a + b;
    },
    subtract: function(a, b) {
        return a - b;
    }
};
console.log(calculator.add(5, 3));      // แสดง: 8
console.log(calculator.subtract(5, 3));  // แสดง: 2

// 8. Nested Function (Function ซ้อน Function)
function outer(x) {
    function inner(y) {
        return x + y;  // inner function สามารถเข้าถึงตัวแปรของ outer function
    }
    return inner;
}
let addFive = outer(5);
console.log(addFive(3));  // แสดง: 8

// 9. Callback Function
function process(callback) {
    console.log("กำลังประมวลผล...");
    callback();  // เรียกใช้ function ที่ส่งเข้ามา
}
process(function() {
    console.log("เสร็จสิ้น!");
});

// 10. Immediately Invoked Function Expression (IIFE)
(function() {
    console.log("Function นี้ทำงานทันทีที่ถูกประกาศ");
})();
```


### 📝 แบบทดสอบที่ 2.4.1: Functions
1. สร้าง function คำนวณค่า BMI (ดัชนีมวลกาย) จากน้ำหนักและส่วนสูง
2. สร้าง function ที่รับชื่อและอายุ แล้วแสดงข้อความทักทายที่เหมาะสมกับอายุ
3. เขียน function ตรวจสอบรหัสผ่านว่ามีความยาวมากกว่า 8 ตัวอักษรหรือไม่

### บันทึกผลการทดลอง 2.4.1
```js
const calculateBMI = (weight, height) => {
    const bmi = weight / (height * height);
    return `ค่า BMI ของคุณคือ ${bmi.toFixed(2)}`;
};

console.log(calculateBMI(70, 1.75));
```
```js
greetByAge("theeranat", 19);
const greetByAge = (name, age) => {
    let message;
    if (age < 0) {
        message = "กรุณาใส่อายุตัวเลขที่ถูกต้อง";
    } else if (age <= 12) {
        message = `สวัสดีครับ/ค่ะ ${name} คุณยังเป็นเด็กอยู่เลย!`;
    } else if (age <= 19) {
        message = `สวัสดีครับ/ค่ะ ${name} วัยรุ่นไฟแรงเลยนะ!`;
    } else if (age <= 59) {
        message = `สวัสดีครับ/ค่ะ ${name} ขอให้มีความสุขในวัยทำงานนะครับ!`;
    } else {
        message = `สวัสดีครับ/ค่ะ ${name} รักษาสุขภาพในวัยสูงอายุนะครับ!`;
    }
    console.log(message);
};
```
```js
const isValidPassword = password => {
    if (password.length > 8) {
        return "รหัสผ่านปลอดภัย";
    } else {
        return "รหัสผ่านสั้นเกินไป (ต้องมากกว่า 8 ตัวอักษร)";
    }
};

console.log(isValidPassword("qwertyui"));
```
[รูปผลการทดลองที่ 2.4.1]

![image](https://github.com/user-attachments/assets/091a763a-35ea-4f1b-9937-4e401a623ba2)

#### 2.4.2 Arrow Function
Arrow Function เป็นวิธีการเขียน function แบบสั้นๆ ที่มาพร้อมกับ JavaScript เวอร์ชัน ES6

### ตัวอย่างการใช้ Arrow Function
```javascript
// Arrow Function แบบพื้นฐาน
const greet = (name) => {
    return "สวัสดี " + name;
};

// Arrow Function แบบย่อ (ถ้ามีคำสั่งเดียว)
const greetShort = name => "สวัสดี " + name;

// Arrow Function ที่มีหลายพารามิเตอร์
const multiply = (a, b) => a * b;

// Arrow Function ที่ไม่มีพารามิเตอร์
const getRandomNumber = () => Math.random();

// ตัวอย่างการใช้ Arrow Function กับ Array
const numbers = [1, 2, 3, 4, 5];

// การใช้ map กับ Arrow Function
const doubled = numbers.map(num => num * 2);
console.log("เลขคูณ 2:", doubled); // [2, 4, 6, 8, 10]

// การใช้ filter กับ Arrow Function
const evenNumbers = numbers.filter(num => num % 2 === 0);
console.log("เลขคู่:", evenNumbers); // [2, 4]
```
### แบบทดสอบ 2.4.2 เขียนฟังก์ชันต่อไปนี้ในรูปแบบ Arrow function
1. สร้าง function คำนวณค่า BMI (ดัชนีมวลกาย) จากน้ำหนักและส่วนสูง
2. สร้าง function ที่รับชื่อและอายุ แล้วแสดงข้อความทักทายที่เหมาะสมกับอายุ
3. เขียน function ตรวจสอบรหัสผ่านว่ามีความยาวมากกว่า 8 ตัวอักษรหรือไม่

### บันทึกผลการทดลอง 2.4.2
```js
const calculateBMI = (weight, height) => weight / (height ** 2);

console.log(calculateBMI(70, 1.75));
```
```js
const greetByAge = (name, age) => age < 18 ? `สวัสดี ${name}! คุณยังเป็นวัยรุ่นอยู่` : `สวัสดีคุณ ${name}! ยินดีต้อนรับ`;

console.log(greetByAge("theeranat", 12));
```
```js
const isPasswordValid = password => password.length > 8;

console.log(isPasswordValid("qwertyui"));
```
[รูปผลการทดลองที่ 2.4.2]

![image](https://github.com/user-attachments/assets/30bf8854-c3db-4382-9184-085dc70a0327)

## การทดลองที่ 3 : การใช้ JavaScript กับ HTML และ CSS
### การทดลองที่ 3.1 การสร้างปุ่มและจัดการ Event ด้วย JavaScript
### ตัวอย่างที่ 1 
```html
<!DOCTYPE html>
<html>
<head>
    <title>Event Handling</title>
</head>
<body>
    <button onclick="showMessage()">คลิกที่นี่</button>
    
    <script>
    function showMessage() {
        alert("สวัสดีครับ/ค่ะ!");
    }
    </script>
</body>
</html>
```
### ตัวอย่างที่ 2
```html
<!DOCTYPE html>
<html>
<head>
    <title>Event Handling</title>
</head>
<body>
    Enter name<input type="text" id="name">
    <button onclick="showMessage(document.getElementById('name').value)">คลิกที่นี่</button>
    
    <script>
    function showMessage(name) {
        alert("สวัสดีครับ/ค่ะ คุณ :",name);
    }
    </script>
</body>
</html>
```
### ตัวอย่างที่ 3 
```html
<!DOCTYPE html>
<html>
<head>
    <title>Event Handling</title>
</head>
<body>
    Enter name<input type="text" id="name">
    <p id="output_value"></p>
    <button onclick="showMessage(document.getElementById('name').value)">คลิกที่นี่</button>
    
    <script>
    function showMessage(name) {
        document.getElementById('output_value').innerHTML='Hello' + name;
    }
    </script>
</body>
</html>
```

### แบบทดสอบ 3.1 
1. เขียนเว็บ รับค่าน้ำหนักและส่วนสูง ทำการ คำนวณค่า BMI (ดัชนีมวลกาย) แล้วแสดงผลว่า อ้วน, ผอม หรือ สมส่วน โดยเขียนฟังก์ชันแบบ Arrow function

### บันทึกผลการทดลอง 3.1
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BMI</title>
    
    <!-- css -->
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --arial-font: Arial, Helvetica, sans-serif;
            --primary-color: #4CAF50;
            --secondary-color: #f1f1f1;
            --text-color: #333;
            --input-border: #ccc;
            --input-focus: #4CAF50;
            --button-hover: #45a049;
        }

        html {
            font-family: var(--arial-font);
            padding: 20px 100px;
        }

        .title {
            text-align: center;
            color: var(--primary-color);
            margin: 40px;
        }

        .form {
            margin: 15px 0;
            text-align: left;
        }

        label {
            font-weight: bold;
            display: block;
            margin-top: 20px;
            color: var(--text-color);
        }
        
        input {
            width: 100%;
            padding: 10px;
            margin-top: 20px;
            font-size: 16px;
            border: 2px solid var(--input-border);
            border-radius: 5px;
            transition: all 0.3s ease-in-out;
            outline: none;
        }

        input:focus {
            border-color: var(--input-focus);
            box-shadow: 0 0 8px rgba(76, 175, 80, 0.5);
        }

        .button {
            background: var(--primary-color);
            color: white;
            padding: 10px;
            margin: 20px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            cursor: pointer;
            width: 100%;
            transition: background 0.3s ease-in-out;
        }

        .button:hover {
            background: var(--button-hover);
        }

        .result {
            text-align: center;
            margin-top: 20px;
            font-size: 24px;
            font-weight: bold;
        }
    </style>
</head>
<body>
    <h1 class="title">CalculateBMI</h1>
    <hr>
    <form class="form">
        <div class="weight">
            <label for="weight">Input weight (Kilogram)</label>
            <input type="number" name="weight" id="weight">
        </div>
        <!-- <hr> -->
        <div class="height">
            <label for="height">Input height (Meter)</label>
            <input type="number" name="height" id="height">
        </div>
        <button type="button" id="result-btn" class="button" onclick="showBMI()">Submit</button>
    </form>
    <hr>
    <h2 class="result" id="result"></h2>

    <!-- js -->
    <script>
        const calculateBMI = (weight, height) => (weight / (height ** 2)).toFixed(2);

        const showBMI = () => {
        const weight = parseFloat(document.getElementById("weight").value);
        const height = parseFloat(document.getElementById("height").value);
        const resultDiv = document.getElementById("result");

        if (!weight || !height || weight <= 0 || height <= 0) {
            resultDiv.innerHTML = `<span style="color: red;">กรุณากรอกข้อมูลให้ถูกต้อง</span>`;
            return;
        }

        const bmi = calculateBMI(weight, height);
        let message = "";

        if (bmi < 18.5) {
            message = "คุณน้ำหนักต่ำกว่ามาตรฐาน (ผอม)";
        } else if (bmi < 24.9) {
            message = "คุณน้ำหนักปกติ";
        } else if (bmi < 29.9) {
            message = "น้ำหนักเกิน (ท้วม)";
        } else if (bmi < 34.9) {
            message = "โรคอ้วนระดับ 1";
        } else if (bmi < 39.9) {
            message = "โรคอ้วนระดับ 2";
        } else {
            message = "โรคอ้วนระดับ 3 (อันตรายมาก)";
        }

        resultDiv.innerHTML = `ค่า BMI ของคุณคือ: <b>${bmi}</b><br><span>${message}</span>`;
    };
    </script>
</body>
</html>
```
[รูปผลการทดลองที่ 3.1]
![image](https://github.com/user-attachments/assets/59dfe176-ae79-4699-8f4a-4c544ba97fca)

## การทดลองที่ 3.2 : การสร้างฟอร์มสำหรับจองห้องพัก
การสร้างฟอร์มลงทะเบียนเพื่อรวบรวมข้อมูลที่จำเป็นสำหรับการจองห้องพัก

### ขั้นตอนที่ 3.2.1: สร้างโครงสร้าง HTML พื้นฐาน

สร้างไฟล์ `index.html` และใส่โค้ดต่อไปนี้:

```html
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบจองห้องพักออนไลน์</title>
</head>
<body>
    <h1>แบบฟอร์มจองห้องพัก</h1>
    
    <form id="bookingForm">
        <div>
            <label for="fullname">ชื่อ-นามสกุล:</label>
            <input type="text" id="fullname" name="fullname" required>
        </div>

        <div>
            <label for="email">อีเมล:</label>
            <input type="email" id="email" name="email" required>
        </div>

        <div>
            <label for="phone">เบอร์โทรศัพท์:</label>
            <input type="tel" id="phone" name="phone" required>
        </div>

        <div>
            <label for="checkin">วันที่เช็คอิน:</label>
            <input type="date" id="checkin" name="checkin" required>
        </div>

        <div>
            <label for="checkout">วันที่เช็คเอาท์:</label>
            <input type="date" id="checkout" name="checkout" required>
        </div>

        <div>
            <label for="roomtype">ประเภทห้องพัก:</label>
            <select id="roomtype" name="roomtype" required>
                <option value="">กรุณาเลือกประเภทห้องพัก</option>
                <option value="standard">ห้องมาตรฐาน</option>
                <option value="deluxe">ห้องดีลักซ์</option>
                <option value="suite">ห้องสวีท</option>
            </select>
        </div>

        <div>
            <label for="guests">จำนวนผู้เข้าพัก:</label>
            <input type="number" id="guests" name="guests" min="1" max="4" required>
        </div>

        <button type="submit">จองห้องพัก</button>
    </form>
</body>
</html>
```

### ขั้นตอนที่ 3.2.2 : การปรับแต่งด้วย CSS

เพิ่มความสวยงามให้กับฟอร์มด้วย CSS โดยเพิ่ม `<style>` ในส่วน `<head>` ของไฟล์ HTML:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบจองห้องพักออนไลน์</title>
    <style>
        body {
            font-family: 'Sarabun', sans-serif;
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f5f5f5;
        }

        h1 {
            color: #2c3e50;
            text-align: center;
            margin-bottom: 30px;
        }

        form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        div {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            color: #34495e;
            font-weight: bold;
        }

        input, select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            box-sizing: border-box;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #3498db;
            box-shadow: 0 0 5px rgba(52,152,219,0.3);
        }

        button {
            background-color: #2980b9;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
        }

        button:hover {
            background-color: #3498db;
        }

        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
        }
    </style>
</head>
```

### คำอธิบาย CSS:

1. ใช้ `max-width` และ `margin: 0 auto` เพื่อจัดกึ่งกลางฟอร์ม
2. จัดการ layout ด้วย `display: block` และ `width: 100%`
3. เพิ่มเอฟเฟกต์ `hover` และ `focus`
4. ใช้ `box-shadow` เพื่อเพิ่มมิติการแสดงผล
5. รองรับการแสดงผลบนมือถือด้วย `@media`

### ผลการทดลอง
ทดสอบปรับแต่ง CSS ในแต่ละส่วน แล้วเขียน สรุปผลการทดลองว่าได้ทดลองเปลี่ยนส่วนใด แล้วผลเป็นอย่างไร พร้อมแนบรูปประกอบการทดลอง

### บันทึกผลการทดลอง 3.2.2
```html
<style>
        @import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

        :root {
            --kanit-font: "Kanit", serif;
            --sakura-pink: #ffb7c5;
            --sakura-light-pink: #ffd9e3;
            --sakura-dark-pink: #e56a89;
            --sakura-white: #fff0f5;
            --sakura-brown: #8b5a2b;
            --primary-color: #ff6b81;
            --secondary-color: #f8c8dc;
            --background-color: #fffafc;
            --text-color: #333;
            --border-color: #e0a3b6;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--kanit-font);
            max-width: 600px;
            margin: 0 auto;
            padding: 15px;
            background-color: var(--background-color);
        }

        h1 {
            color: var(--text-color);
            text-align: center;
            margin-bottom: 30px;
        }

        form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 10px 10px 30px 0 var(--sakura-light-pink);
        }

        div {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            color: var(--text-color);
            font-weight: bold;
        }

        input, 
        select {
            width: 100%;
            padding: 8px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            box-sizing: border-box;
        }

        input:focus, 
        select:focus {
            outline: none;
            border-color: var(--sakura-dark-pink);
            box-shadow: 0 0 5px var(--border-color);
        }

        button {
            background-color: var(--sakura-dark-pink);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
        }

        button:hover {
            background-color: var(--sakura-pink);
            color: var(--text-color);
        }

        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
        }
    </style>
```
การปรับเปลี่ยน css

1. การใช้ Kanit Font จาก https://fonts.google.com/ รูปแบบของ import url
2. จาก set up ทุก element ให้มี margin 0, padding 0, box-sizing border-box
3. การใช้ :root เพื่อ set up ค่าต่างๆ เช่น font-family, color
4. การปรับแต่งสีต่างๆ ทั้ง background form text button และ :hover, :focus

[รูปผลการทดลองที่ 3.2.2]
![image](https://github.com/user-attachments/assets/9cb0c136-1ecf-4dc9-8aed-0c98e1f73e73)


## ขั้นตอนที่ 3.2.3: การเพิ่มฟังก์ชันด้วย JavaScript

เพิ่มโค้ด JavaScript ก่อนปิด `</body>`:

```html
<script>
    document.getElementById('bookingForm').addEventListener('submit', function(e) {
        e.preventDefault();
        
        // ตรวจสอบวันที่
        const checkin = new Date(document.getElementById('checkin').value);
        const checkout = new Date(document.getElementById('checkout').value);
        const today = new Date();
        
        if (checkin < today) {
            alert('กรุณาเลือกวันเช็คอินที่ยังไม่ผ่านมา');
            return;
        }
        
        if (checkout <= checkin) {
            alert('วันเช็คเอาท์ต้องมาหลังวันเช็คอิน');
            return;
        }
        
        // ตรวจสอบรูปแบบเบอร์โทร
        const phone = document.getElementById('phone').value;
        const phoneRegex = /^[0-9]{10}$/;
        if (!phoneRegex.test(phone)) {
            alert('กรุณากรอกเบอร์โทรศัพท์ให้ถูกต้อง (10 หลัก)');
            return;
        }
        
        // คำนวณจำนวนวันที่พัก
        const days = Math.ceil((checkout - checkin) / (1000 * 60 * 60 * 24));
        
        // แสดงสรุปการจอง
        const roomtype = document.getElementById('roomtype');
        const roomtypeText = roomtype.options[roomtype.selectedIndex].text;
        
        const summary = `
            สรุปการจอง:
            - ชื่อผู้จอง: ${document.getElementById('fullname').value}
            - ประเภทห้อง: ${roomtypeText}
            - วันที่เข้าพัก: ${checkin.toLocaleDateString('th-TH')}
            - วันที่ออก: ${checkout.toLocaleDateString('th-TH')}
            - จำนวนวันที่พัก: ${days} วัน
            - จำนวนผู้เข้าพัก: ${document.getElementById('guests').value} ท่าน
        `;
        
        if (confirm(summary + '\n\nยืนยันการจองห้องพัก?')) {
            alert('จองห้องพักเรียบร้อยแล้ว');
            this.reset();
        }
    });

    // เพิ่มการตรวจสอบวันที่แบบ Real-time
    document.getElementById('checkin').addEventListener('change', function() {
        document.getElementById('checkout').min = this.value;
    });

    // จำกัดจำนวนผู้เข้าพักตามประเภทห้อง
    document.getElementById('roomtype').addEventListener('change', function() {
        const guestsInput = document.getElementById('guests');
        if (this.value === 'standard') {
            guestsInput.max = 2;
        } else if (this.value === 'deluxe') {
            guestsInput.max = 3;
        } else if (this.value === 'suite') {
            guestsInput.max = 4;
        }
        
        if (guestsInput.value > guestsInput.max) {
            guestsInput.value = guestsInput.max;
        }
    });
</script>
```

### คำอธิบาย JavaScript:

1. ตรวจสอบความถูกต้องของข้อมูล:
   - วันที่เช็คอินต้องไม่เป็นวันที่ผ่านมาแล้ว
   - วันที่เช็คเอาท์ต้องมาหลังวันเช็คอิน
   - เบอร์โทรศัพท์ต้องมี 10 หลัก

2. เพิ่มฟังก์ชันการโต้ตอบ:
   - แสดงสรุปการจองก่อนยืนยัน
   - รีเซ็ตฟอร์มหลังการจอง
   - ปรับจำนวนผู้เข้าพักตามประเภทห้อง

3. การตรวจสอบแบบ Real-time:
   - ตรวจสอบวันที่เช็คอิน-เช็คเอาท์
   - ปรับจำนวนผู้เข้าพักสูงสุดตามประเภทห้อง
</body>
</html>
```

### ผลการทดลอง
ทดสอบปรับแต่ง JavaScript ในแต่ละส่วน แล้วอธิบายโค้ดในแต่ละส่วน เขียนสรุปผลการทดลองว่าได้ทดลองเปลี่ยนส่วนใด แล้วผลเป็นอย่างไร พร้อมแนบรูปประกอบการทดลอง

### บันทึกผลการทดลอง 3.2.3
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

    <!-- css -->
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Kanit:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

        :root {
            --kanit-font: "Kanit", serif;
            --sakura-pink: #ffb7c5;
            --sakura-light-pink: #ffd9e3;
            --sakura-dark-pink: #e56a89;
            --sakura-white: #fff0f5;
            --sakura-brown: #8b5a2b;
            --primary-color: #ff6b81;
            --secondary-color: #f8c8dc;
            --background-color: #fffafc;
            --text-color: #333;
            --border-color: #e0a3b6;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: var(--kanit-font);
            max-width: 600px;
            margin: 0 auto;
            padding: 15px;
            background-color: var(--background-color);
        }

        h1 {
            color: var(--text-color);
            text-align: center;
            margin-bottom: 30px;
        }

        form {
            background-color: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 10px 10px 30px 0 var(--sakura-light-pink);
        }

        div {
            margin-bottom: 15px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            color: var(--text-color);
            font-weight: bold;
        }

        input, 
        select {
            width: 100%;
            padding: 8px;
            border: 1px solid var(--border-color);
            border-radius: 4px;
            box-sizing: border-box;
        }

        input:focus, 
        select:focus {
            outline: none;
            border-color: var(--sakura-dark-pink);
            box-shadow: 0 0 5px var(--border-color);
        }

        button {
            background-color: var(--sakura-dark-pink);
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
        }

        button:hover {
            background-color: var(--sakura-pink);
            color: var(--text-color);
        }

        @media (max-width: 480px) {
            body {
                padding: 10px;
            }
        }
    </style>
<body>
    <h1>แบบฟอร์มจองห้องพัก</h1>
    
    <form id="bookingForm">
        <div>
            <label for="fullname">ชื่อ-นามสกุล:</label>
            <input type="text" id="fullname" name="fullname" required>
        </div>

        <div>
            <label for="email">อีเมล:</label>
            <input type="email" id="email" name="email" required>
        </div>

        <div>
            <label for="phone">เบอร์โทรศัพท์:</label>
            <input type="tel" id="phone" name="phone" required>
        </div>

        <div>
            <label for="checkin">วันที่เช็คอิน:</label>
            <input type="date" id="checkin" name="checkin" required>
        </div>

        <div>
            <label for="checkout">วันที่เช็คเอาท์:</label>
            <input type="date" id="checkout" name="checkout" required>
        </div>

        <div>
            <label for="roomtype">ประเภทห้องพัก:</label>
            <select id="roomtype" name="roomtype" required>
                <option value="">กรุณาเลือกประเภทห้องพัก</option>
                <option value="single">ห้องพักสำหรับ 1 คน เตียงเดี่ยว 1 เตียง</option>
                <option value="double">ห้องพักสำหรับ 2 คน เตียงเดี่ยวขนาดใหญ่ 1 เตียง</option>
                <option value="twin">ห้องพักสำหรับ 2 คน เตียงเดี่ยว 2 เตียง แยกจากกัน</option>
                <option value="triple">ห้องพักสำหรับ 3 คน เตียง 3 เตียง </option>
                <option value="quad">ห้องพักสำหรับ 4 คน เตียงเดี่ยว 4 เตียง</option>
            </select>
        </div>

        <div>
            <label for="guests">จำนวนผู้เข้าพัก:</label>
            <input type="number" id="guests" name="guests" min="1" max="4" required>
        </div>

        <button type="submit">จองห้องพัก</button>
    </form>

    <!-- js -->
    <script>
        document.getElementById('bookingForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // ตรวจสอบวันที่
            const checkin = new Date(document.getElementById('checkin').value);
            const checkout = new Date(document.getElementById('checkout').value);
            const today = new Date();
            
            if (checkin < today) {
                alert('กรุณาเลือกวันเช็คอินที่ยังไม่ผ่านมา');
                return;
            }
            
            if (checkout <= checkin) {
                alert('วันเช็คเอาท์ต้องมาหลังวันเช็คอิน');
                return;
            }
            
            // ตรวจสอบรูปแบบเบอร์โทร
            const phone = document.getElementById('phone').value;
            const phoneRegex = /^[0-9]{10}$/;
            if (!phoneRegex.test(phone)) {
                alert('กรุณากรอกเบอร์โทรศัพท์ให้ถูกต้อง (10 หลัก)');
                return;
            }
            
            // คำนวณจำนวนวันที่พัก
            const days = Math.ceil((checkout - checkin) / (1000 * 60 * 60 * 24));
            
            // แสดงสรุปการจอง
            const roomtype = document.getElementById('roomtype');
            const roomtypeText = roomtype.options[roomtype.selectedIndex].text;
            
            const summary = `
                สรุปการจอง:
                - ชื่อผู้จอง: ${document.getElementById('fullname').value}
                - ประเภทห้อง: ${roomtypeText}
                - วันที่เข้าพัก: ${checkin.toLocaleDateString('th-TH')}
                - วันที่ออก: ${checkout.toLocaleDateString('th-TH')}
                - จำนวนวันที่พัก: ${days} วัน
                - จำนวนผู้เข้าพัก: ${document.getElementById('guests').value} ท่าน
                - ขอบคุณที่เลือกใข้บริการของเรา
            `;
            
            if (confirm(summary + '\n\nยืนยันการจองห้องพัก?')) {
                alert('จองห้องพักเรียบร้อยแล้ว');
                this.reset();
            }
        });
    
        // เพิ่มการตรวจสอบวันที่แบบ Real-time
        document.getElementById('checkin').addEventListener('change', function() {
            document.getElementById('checkout').min = this.value;
        });
    
        // จำกัดจำนวนผู้เข้าพักตามประเภทห้อง
        document.getElementById('roomtype').addEventListener('change', function() {
            const guestsInput = document.getElementById('guests');
            if (this.value === 'single') {
                guestsInput.max = 1;
            } else if (this.value === 'double') {
                guestsInput.max = 2;
            } else if (this.value === 'twin') {
                guestsInput.max = 2;
            } else if (this.value === 'triple') {
                guestsInput.max = 3;
            } else if (this.value === 'quad') {
                guestsInput.max = 4;
            } 
            
            if (guestsInput.value > guestsInput.max) {
                guestsInput.value = guestsInput.max;
            }
        });
    </script>
</body>
</html>
```

การปรับเปลี่ยน html

1. ปรับเปลี่ยน form ที่ ประเภทห้องพัก ให้มีประเภท 5 ประเภท

การปรับเปลี่ยน js

1. ปรับเปลี่ยนการจำกัดจำนวนผู้เข้าพักในแต่ละประเภทของห้องพัก

[รูปผลการทดลองที่ 3.2.3]
![image](https://github.com/user-attachments/assets/5ca60007-cb5c-40d6-8dff-e7a0b3429ddd)

![image](https://github.com/user-attachments/assets/0b96082c-565f-4265-b52f-08cde44cfc9f)


## คำแนะนำเพิ่มเติม
- ทดลองเขียนโค้ดทุกตัวอย่างด้วยตัวเอง
- ลองปรับเปลี่ยนค่าต่างๆ เพื่อดูผลลัพธ์ที่เปลี่ยนไป
- ใช้ Console ใน Developer Tools ของเบราว์เซอร์เพื่อดูผลลัพธ์และแก้ไขข้อผิดพลาด
- ทำความเข้าใจแต่ละบรรทัดของโค้ดก่อนที่จะไปศึกษาหัวข้อถัดไป (ใช้ GenAI เพื่อช่วยในการอธิบายได้)

## แหล่งเรียนรู้เพิ่มเติม
- MDN Web Docs: https://developer.mozilla.org/th/docs/Web/JavaScript
- W3Schools: https://www.w3schools.com/js/
- JavaScript.info: https://javascript.info/
