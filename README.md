# คอมพิวเตอร์ฮับ - เว็บไซต์ร้านขายคอมพิวเตอร์

เว็บไซต์ร้านขายคอมพิวเตอร์ครบวงจร สร้างด้วย HTML และ CSS เท่านั้น ไม่มีการใช้ JavaScript หรือ Framework ใดๆ

## โครงสร้างไฟล์และโฟลเดอร์

```
Web Project 1/
|── css/
│   └── style.css       # ไฟล์ CSS หลัก
├── images/             # โฟลเดอร์สำหรับเก็บรูปภาพ
├── contact.html        # หน้าติดต่อเรา
├── index.html          # หน้าแรก
├── menu.html           # หน้าสินค้า
└── README.md           # ไฟล์อธิบายการทำงาน
```

## 1. การทำงานของ HTML และ CSS ในส่วนหลักๆ

### โครงสร้าง Semantic HTML

เว็บไซต์ใช้ Semantic HTML เพื่อให้โครงสร้างมีความชัดเจนและ SEO-friendly:

- `<header>`: ส่วนหัวของเว็บไซต์ บรรจุ Navbar
- `<nav>`: เมนูนำทาง
- `<main>`: เนื้อหาหลักของแต่ละหน้า
- `<section>`: แบ่งเนื้อหาเป็นส่วนๆ
- `<footer>`: ส่วนท้ายของเว็บไซต์

### Flexbox Layout (ใช้ 2 จุด)

**จุดที่ 1: Navbar**
```css
.navbar {
    display: flex;
    justify-content: space-between;  /* จัด logo ชิดซ้าย, เมนูชิดขวา */
    align-items: center;              /* จัดแนวแกนกลางให้ตรงกัน */
}
```
- ใช้ Flexbox ในการจัด layout ของ Navbar
- `justify-content: space-between` ทำให้ logo อยู่ชิดซ้าย และเมนูลิงก์อยู่ชิดขวา
- `align-items: center` จัดให้องค์ประกอบทั้งหมดอยู่ตรงกลางแนวตั้ง

**จุดที่ 2: Nav Links**
```css
.navbar .nav-links {
    display: flex;
    gap: 2rem;  /* ระยะห่างระหว่างลิงก์แต่ละอัน */
}
```
- ใช้ Flexbox ในการจัดเรียงลิงก์เมนูแบบแนวนอน
- `gap: 2rem` กำหนดระยะห่างระหว่างลิงก์แต่ละอัน

### CSS Grid Layout (ใช้ 3 จุด)

**จุดที่ 1: Features Grid**
```css
.features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
}
```
- ใช้ Grid ในการจัดการ์ดจุดเด่น 3 ใบ
- `repeat(auto-fit, minmax(280px, 1fr))` ทำให้การ์ดปรับขนาดอัตโนมัติตามหน้าจอ
- ขั้นต่ำ 280px และขยายเต็มความกว้างที่เหลือ

**จุดที่ 2: Testimonials Grid**
```css
.testimonials-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}
```
- ใช้ Grid ในการจัดรีวิวลูกค้า 2 รีวิว
- ขั้นต่ำ 300px และขยายเต็มความกว้างที่เหลือ

**จุดที่ 3: Products Grid**
```css
.products-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}
```
- ใช้ Grid ในการจัดการ์ดสินค้า 6 ใบ
- ขั้นต่ำ 300px และขยายเต็มความกว้างที่เหลือ
- รองรับการแสดงผลอย่างน้อย 3 คอลัมน์บนหน้าจอขนาดใหญ่

**จุดที่ 4: Contact Container**
```css
.contact-container {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
}
```
- ใช้ Grid ในการจัดข้อมูลติดต่อและแบบฟอร์ม
- แบ่งเป็น 2 คอลัมน์เท่าๆ กัน (1fr 1fr)

## 2. วิธีการกำหนด CSS Variables

CSS Variables หรือ Custom Properties ถูกกำหนดไว้ที่ `:root` selector เพื่อใช้งานทั่วทั้งเว็บไซต์:

```css
:root {
    --primary-color: #2563eb;      /* สีหลัก - สีน้ำเงิน */
    --secondary-color: #1e40af;    /* สีรอง - สีน้ำเงินเข้ม */
    --accent-color: #f59e0b;       /* สีเน้น - สีส้ม */
    --text-dark: #1f2937;          /* สีข้อความหลัก */
    --text-light: #6b7280;         /* สีข้อความรอง */
    --bg-light: #f9fafb;           /* สีพื้นหลังอ่อน */
    --bg-white: #ffffff;          /* สีพื้นหลังขาว */
    --border-color: #e5e7eb;       /* สีเส้นขอบ */
}
```

### ข้อดีของการใช้ CSS Variables:

1. **Consistency**: สีทั้งหมดใช้ตัวแปรเดียวกัน ทำให้สีสม่ำเสมอทั้งเว็บ
2. **Easy Maintenance**: ถ้าต้องการเปลี่ยนโทนสี แก้ที่ `:root` ที่เดียว ไม่ต้องแก้ทีละจุด
3. **Reusability**: สามารถเรียกใช้ตัวแปรได้ทุกที่ใน CSS

### วิธีการใช้งาน:

```css
.hero {
    background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
}

.btn-cta {
    background-color: var(--accent-color);
    color: var(--bg-white);
}
```

ใช้ฟังก์ชัน `var()` เพื่อเรียกใช้ตัวแปรที่กำหนดไว้

## 3. ภาพรวมการทำให้เว็บรองรับมือถือ (Responsive Design)

เว็บไซต์ใช้ Media Queries เพื่อทำให้เว็บรองรับหน้าจอขนาดต่างๆ:

### Media Query สำหรับ Tablet (max-แ: 768px)

```css
@media (max-width: 768px) {
    /* Navbar เปลี่ยนเป็นแนวตั้ง */
    .navbar {
        flex-direction: column;
        gap: 1rem;
    }

    /* Grid ทั้งหมดเปลี่ยนเป็น 1 คอลัมน์ */
    .features-grid,
    .testimonials-grid,
    .products-grid {
        grid-template-columns: 1fr;
    }

    /* Contact เปลี่ยนเป็น 1 คอลัมน์ */
    .contact-container {
        grid-template-columns: 1fr;
    }

    /* ปรับขนาดฟอนต์ให้เล็กลง */
    .hero h1 {
        font-size: 2rem;
    }
}
```

### Media Query สำหรับ Mobile (max-width: 480px)

```css
@media (max-width: 480px) {
    /* ลด padding ของ Navbar */
    .navbar {
        padding: 1rem;
    }

    /* ลดขนาดฟอนต์ logo */
    .navbar .logo {
        font-size: 1.25rem;
    }

    /* ลดขนาดฟอนต์ลิงก์ */
    .navbar .nav-links a {
        padding: 0.4rem 0.8rem;
        font-size: 0.9rem;
    }

    /* ลด padding ของ Hero */
    .hero {
        padding: 3rem 1rem;
    }

    /* ลดขนาดฟอนต์หัวข้อหลัก */
    .hero h1 {
        font-size: 1.5rem;
    }

    /* ลด padding ของ section ต่างๆ */
    .features,
    .testimonials,
    .products,
    .contact {
        padding: 2rem 1rem;
    }
}
```

### หลักการ Responsive Design ที่ใช้:

1. **Mobile-First Approach**: เริ่มจากการออกแบบสำหรับหน้าจอเล็กก่อน แล้วค่อยปรับสำหรับหน้าจอใหญ่
2. **Flexible Grid**: ใช้ `repeat(auto-fit, minmax(...))` เพื่อให้ Grid ปรับขนาดอัตโนมัติ
3. **Flexible Typography**: ปรับขนาดฟอนต์ตามขนาดหน้าจอ
4. **Breakpoints**: กำหนดจุดตัดที่ 768px (Tablet) และ 480px (Mobile)

## คุณสมบัติเพิ่มเติม (Bonus Features)

### 1. Google Fonts
- ใช้ฟอนต์ "Sarabun" จาก Google Fonts สำหรับการแสดงผลภาษาไทย
- นำเข้าด้วย `@import url('https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap');`

### 2. Hover Effects
- ทุกปุ่มและลิงก์มี hover effect
- ใช้ `transition: all 0.3s ease` เพื่อให้การเปลี่ยนแปลงนุ่มนวล
- ตัวอย่าง:
  ```css
  .btn-cta:hover {
      background-color: #d97706;
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(245, 158, 11, 0.4);
  }
  ```

### 3. Card Hover Effects
- การ์ดสินค้าและการ์ดจุดเด่นมี hover effect
- เมื่อ hover การ์ดจะลอยขึ้นและเพิ่มเงา
  ```css
  .product-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 12px 32px rgba(0, 0, 0, 0.2);
  }
  ```

### 4. Form Styling
- แบบฟอร์มติดต่อมีการตกแต่งครบถ้วน
- ทุกช่องมี `<label>` กำกับ
- มี focus state เมื่อคลิกที่ช่อง
  ```css
  .form-group input:focus {
      outline: none;
      border-color: var(--primary-color);
      box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
  }
  ```

### 5. Semantic Images
- ทุกรูปมี attribute `alt` เพื่อ accessibility
- รูปโปรไฟล์ใช้ `border-radius: 50%` เพื่อทำเป็นวงกลม
