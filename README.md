# Saki Web

เว็บจัดการสินค้า พัฒนาด้วย Next.js, MongoDB และ Cloudinary

## ความต้องการ

- Node.js 20 ขึ้นไป
- MongoDB connection string
- บัญชี Cloudinary

## ติดตั้งและเริ่มระบบ

```bash
npm install
npm run dev
```

เปิด `http://localhost:3000` แล้วไปที่ `/admin/products` เพื่อเพิ่มสินค้า

## Environment variables

สร้างไฟล์ `.env` ที่ root ของโปรเจกต์ โดยแต่ละตัวแปรต้องอยู่คนละบรรทัด:

```env
MONGODB_URI=mongodb+srv://...
JWT_SECRET=replace-with-a-long-random-secret
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
```

หา `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY` และ `CLOUDINARY_API_SECRET` ได้จาก Cloudinary Console > Settings > API Keys

หลังแก้ `.env` ต้องหยุดและเริ่ม `npm run dev` ใหม่ เพื่อให้ Next.js โหลดค่าใหม่

## การอัปโหลดรูปสินค้า

- รองรับ JPEG, PNG และ WebP
- ขนาดไฟล์สูงสุด 10 MB
- รูปถูกจัดเก็บที่ Cloudinary ในโฟลเดอร์ `ecommerce/products`

### แก้ปัญหา `403` จาก Cloudinary

ตรวจสอบว่าไฟล์ `.env` ไม่ได้เป็นบรรทัดเดียวที่มีข้อความ `\n` คั่นอยู่ ต้องเป็นบรรทัดจริงตามตัวอย่างด้านบน หากยังพบปัญหา ให้คัดลอก API credentials ชุดใหม่จาก Cloudinary Console แล้ว restart development server
