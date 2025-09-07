## MaskedLM-Models

### 🔹 نحوه استفاده از مدل های MaskedLM برای تسک حدس زدن کلمات حذف شده

     tokenizer = AutoTokenizer.from_pretrained(model_name)
     model = AutoModelForMaskedLM.from_pretrained(model_name) 
    
     nlp_fill = pipeline("fill-mask", model=model, tokenizer=tokenizer)
     results = nlp_fill(text) 
     
     print(f"{r['sequence']} (prob={r['score']:.4f})") 

 
### 🔹 خانواده‌ی اصلی BERT برای Mask Prediction
#### 1. BERT (Original)

معماری:

BERT-base: مدل 12 لایه ای 

BERT-large: مدل 24 لایه ای

تسک : Masked LM + Next Sentence Prediction (NSP).

کاربرد : classification, NER, QA, embeddings.

#### 2. RoBERTa (Robustly Optimized BERT)

تغییرات مهم:

حذف NSP → فقط Masked LM.

آموزش روی دیتاست بزرگ‌تر و طولانی‌تر.

معماری همون BERTه، ولی بهینه‌تر.

در خیلی از بنچمارک‌ها از BERT جلو زد.

#### 3. DistilBERT

نسخه کوچک‌تر و سبک‌تر BERT (تقریباً نصف پارامترها).

سرعت inference دو برابر، دقت نزدیک به BERT-base.

خیلی مناسب برای لپ‌تاپ یا موبایل.

#### 4. ALBERT (A Lite BERT)

نوآوری: اشتراک‌گذاری وزن‌ها بین لایه‌ها → تعداد پارامتر کمتر، حافظه کمتر.

نسخه‌ی سبک ولی همچنان قوی.

#### 5. ELECTRA

فرق اصلی: به جای MLM، از Replaced Token Detection استفاده می‌کنه.

سریع‌تر و کارآمدتر از BERT در آموزش.

معماری انکودر داره، برای درک متن خیلی خوبه.

#### 6. SpanBERT

تغییر در pretraining: به جای ماسک کردن توکن‌های جدا، کل اسپن‌ها (توالی چندکلمه‌ای) ماسک می‌شن.

بهتر برای QA و coreference resolution.

#### 7. MiniLM

نسخه بسیار کوچک ولی با نگه داشتن کیفیت attention.

عالی برای استفاده در سیستم‌های real-time.

### 🔹 جمع‌بندی در قالب جدول

| مدل            | سایز/لایه                  | ویژگی کلیدی              | بهینه برای     |
| -------------- | -------------------------- | ------------------------ | -------------- |
| **BERT**       | Base (110M) / Large (340M) | اولین MLM، با NSP        | همه‌کاره       |
| **RoBERTa**    | Base / Large               | حذف NSP، دیتای بیشتر     | دقت بالاتر     |
| **DistilBERT** | 66M                        | سبک و سریع               | موبایل/لپ‌تاپ  |
| **ALBERT**     | Base / Large               | اشتراک وزن‌ها            | حافظه کمتر     |
| **ELECTRA**    | Small / Base / Large       | Replaced Token Detection | آموزش سریع‌تر  |
| **SpanBERT**   | Base / Large               | ماسک اسپن‌ها             | QA, NER        |
| **MiniLM**     | کوچک                       | attention-efficient      | real-time apps |



