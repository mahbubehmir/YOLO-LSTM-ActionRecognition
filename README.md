
# تشخیص حرکات ورزشی با YOLOv8، MediaPipe و مدل LSTM

**سیستم هوشمند تشخیص و طبقه‌بندی حرکات ورزشی از روی ویدیوهای تصویری با استفاده از تکنولوژی بینایی ماشین**

---

## 📋 معرفی پروژه

در این پروژه، یک سیستم مبتنی بر هوش مصنوعی طراحی شده که قادر است با دریافت ویدیوهای ورزشی، نوع حرکات انجام‌شده (مانند اسکوات، پوش‌آپ، لانج و ...) را به‌صورت بلادرنگ شناسایی و طبقه‌بندی کند. این سیستم ترکیبی از چند تکنیک مدرن در بینایی ماشین و یادگیری عمیق است:

- **YOLOv8** برای تشخیص مکان ورزشکار در تصویر
- **MediaPipe Pose** برای استخراج نقاط کلیدی بدن (pose estimation)
- **Lucas-Kanade Optical Flow** برای دنبال‌کردن حرکات نقاط کلیدی
- **LSTM (Long Short-Term Memory)** برای تحلیل دنباله‌ای مختصات بدن و پیش‌بینی نوع حرکت

---

## 🎯 کاربردها

این سیستم می‌تواند در زمینه‌های متعددی مورد استفاده قرار گیرد، از جمله:

- 🎽 **برنامه‌های تمرینی خانگی هوشمند**: بررسی و اصلاح فرم حرکات ورزشکار در خانه
- 🏋️‍♂️ **باشگاه‌های ورزشی و مربیگری مجازی**: پایش خودکار عملکرد و پیشرفت ورزشکاران
- 📊 **تحلیل داده‌های ورزشی**: استخراج ویژگی‌های بیومکانیکی از حرکت بدن
- 👨‍⚕️ **فیزیوتراپی و بازتوانی**: بررسی دقیق حرکات بیمار در طول جلسات تمرینی
- 🧠 **پژوهش‌های علوم اعصاب و حرکت‌شناسی**: تجزیه‌وتحلیل دقیق داده‌های حرکتی

---

## 🗂 ساختار پوشه‌ها

```
.
├── notebooks/
│   └── action_recognition.ipynb    # کد اصلی و توضیحات گام‌به‌گام
├── models/
│   ├── lstm_model.h5               # مدل LSTM آموزش‌دیده
│   ├── lstm_scaler.pkl             # StandardScaler برای نرمال‌سازی داده‌ها
│   └── label_encoder.pkl           # LabelEncoder برای بازگردانی نام حرکت
├── data/
│   ├── raw_videos/                 # ویدیوهای ورودی (فرمت mp4 یا avi)
│   └── landmarks_csv/              # خروجی فایل‌های CSV نقاط کلیدی
├── requirements.txt                # کتابخانه‌های مورد نیاز
└── README.md                       # این فایل
```

---

## ⚙️ پیش‌نیازها و نصب

### 1. کلون کردن پروژه
```bash
git clone https://github.com/<username>/<repo-name>.git
cd <repo-name>
```

### 2. ایجاد و فعال‌سازی محیط مجازی
```bash
python -m venv venv
source venv/bin/activate      # در لینوکس / مک
venv\Scripts\activate       # در ویندوز
```

### 3. نصب وابستگی‌ها
```bash
pip install -r requirements.txt
```

---

## 🚀 نحوه اجرا

### گام 1: استخراج نقاط کلیدی بدن از ویدیو
```bash
python extract_landmarks.py --input_dir data/raw_videos --output_dir data/landmarks_csv
```

### گام 2: پیش‌بینی حرکت از روی نقاط کلیدی
```bash
python predict_action.py --model models/lstm_model.h5 --scaler models/lstm_scaler.pkl --labels models/label_encoder.pkl --source path/to/video_or_camera_index
```

---

## 📖 نمونه خروجی

![نمونه خروجی](docs/sample_output.png)

در خروجی نهایی، نوع حرکت شناسایی‌شده روی ویدیو چاپ شده و نقاط کلیدی بدن نیز نمایش داده می‌شوند.

---

## ✍️ توضیح فایل‌ها

- `action_recognition.ipynb`: دفترچه یادداشت اصلی شامل پیاده‌سازی گام به گام
- `extract_landmarks.py`: اسکریپت استخراج مختصات نقاط کلیدی از ویدیوها
- `predict_action.py`: اسکریپت پیش‌بینی نوع حرکت ورزشی با مدل LSTM
- `train_lstm.py`: (اختیاری) آموزش مدل LSTM روی داده‌های حرکتی
- `prepare_dataset.py`: آماده‌سازی فایل‌های CSV برای آموزش مدل

---

## 📄 مجوز

این پروژه تحت مجوز MIT منتشر شده و استفاده آزاد برای مقاصد پژوهشی، آموزشی و تجاری دارد.

---

## 🧠 توسعه‌دهنده محبوبه

-### 📫 راه‌های ارتباطی با من

- 📧 ایمیل: [niayeshmirshekar92@gmail.com](mailto:niayeshmirshekar92@gmail.com)
- 💼 لینکدین: [Mahboubeh Mirshekar](https://www.linkedin.com/in/mahbubeh-mirshekar-999640170)
- اینستاگرام: airobo.project
  کانال تلگرام:airobo_project

---

