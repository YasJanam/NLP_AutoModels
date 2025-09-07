## MaskedLM : Masked Language Models (MLM)

این مدل ها برای **درک متن** خیلی قوی هستند

مدل های MLM برای **فهمیدن** ساخته شدن نه برای **نوشتن** متن

معماری MaskedLM مثل BERT بر پایه‌ی **Encoder-only Transformer** ساخته شده و هدفش **«فهمیدن کل متن به صورت هم‌زمان»** هست، نه **«نوشتن متن به ترتیب»**.

اموزش MLM ها به این صورت هست : در طول آموزش بخشی از جمله را حذف میکنند و مدل باید بخش های حذف شده را حدس بزند. نگاه MLM ها به متن دو طرفه هست ( برعکس مدل های Causal  که تنها به گذشته نگاه میکنند )

خیلی از مدل‌های بزرگ جدید (مثل T5 و BART) ترکیبی از ایده‌های MaskedLM + Seq2Seq هستن : مثلا مدل های بارت قبل از آموزش، پیش آموزش میشوند تا جای خالی جملات را حدس بزنند

در جدول زیر یک مقایسه بین MLM ها و مدل های علی را میبینید

#### MaskedLM vs CausalLM

| ویژگی            | CausalLM (مثل GPT)        | MaskedLM (مثل BERT)           |
| ---------------- | ------------------------- | ----------------------------- |
| **جهت**          | یک‌طرفه (چپ→راست)         | دوطرفه (چپ و راست)            |
| **تمرکز اصلی**   | تولید متن (generation)    | درک متن (understanding)       |
| **کاربردها**     | چت‌بات، نویسندگی، کدنویسی | طبقه‌بندی، QA، NER، embedding |
| **نمونه مدل‌ها** | GPT-2, GPT-Neo, OPT       | BERT, RoBERTa, DistilBERT     |


#### 🔹 معروف‌ترین مدل‌های MaskedLM

BERT (Bidirectional Encoder Representations from Transformers) → پایه‌گذار اصلی

RoBERTa → BERT نسخه بهینه‌تر و بزرگ‌تر از 

ALBERT → سبک‌تر با پارامترهای اشتراکی

DistilBERT → نسخه کوچک‌تر و سریع‌تر برای کاربردهای عملی

ELECTRA → به جای پیش‌بینی ماسک، روی تشخیص «جعلی یا واقعی بودن توکن» آموزش می‌بینه (کارآمدتر)


## 🔹 معماری پایه BERT-style ) MaskedLM )

#### 1. Encoder-only Transformer

مدل های MaskedLM فقط از بخش Encoder ترنسفورمر استفاده می‌کنن

برخلاف GPT (که فقط Decoder هست) یا T5 (Encoder-Decoder)

این یعنی هر توکن می‌تونه هم به گذشته و هم به آینده نگاه کنه (bidirectional)

#### 2. ورودی

توکن‌ها (subword یا wordpiece) به embedding تبدیل می‌شن.

سه بخش با هم جمع می‌شن:

Token Embedding (نمایش خود کلمه/ساب‌ ورد)

Position Embedding (موقعیت توکن در جمله)

Segment Embedding ( NLI/QA برای تشخیص جمله‌ی اول و دوم در کارهایی مثل )

#### 3. لایه‌های Encoder

هر لایه‌ی انکودر شامل:

Multi-Head Self-Attention (بدون causal mask → می‌تونه همه توکن‌ها رو ببینه)

Add & Norm (Residual Connection + LayerNorm)

Feed-Forward Network (FFN) ( GELU یا ReLU دو لایه خطی با فعال‌ساز )

Add & Norm (دوباره)

🔁 این ساختار n بار تکرار می‌شه (مثلاً در BERT-base = 12 بار، در BERT-large = 24 بار)

#### 4. خروجی

بردار contextualized برای هر توکن داریم (یعنی نمایش هر کلمه با توجه به کل جمله)

روی توکن‌های ماسک‌شده، یک لایه پیش‌بینی (linear + softmax) قرار می‌گیره تا احتمال کلمه اصلی رو بده

### 🔹 آموزش 
##### Masked Language Modeling (MLM)

حدود ۱۵٪ توکن‌ها ماسک می‌شن.

مدل باید اون‌ها رو پیش‌بینی کنه.

(بعضی وقت‌ها به‌جای [MASK]، همون کلمه اصلی یا یه کلمه تصادفی گذاشته می‌شه -> برای جلوگیری از overfitting).

##### Next Sentence Prediction (NSP) ( اصلی BERT فقط در )

بررسی می‌کنه که آیا جمله‌ی دوم ادامه‌ی جمله‌ی اول هست یا نه.

در مدل‌های بعدی (مثل RoBERTa) حذف شد چون مؤثر نبود.

### 🔹 تفاوت MaskedLM با CausalLM از نظر معماری

| بخش            | MaskedLM (BERT)                      | CausalLM (GPT)                          |
| -------------- | ------------------------------------ | --------------------------------------- |
| ساختار         | Encoder-only                         | Decoder-only                            |
| Self-Attention | همه توکن‌ها به همه دسترسی دارن       | causal mask (توکن فقط گذشته رو می‌بینه) |
| Training       | Masked LM objective (۱۵٪ ماسک)       | Language modeling (پیش‌بینی توکن بعدی)  |
| Embeddings     | Token + Position + Segment           | Token + Position                        |
| خروجی          | بردارهای contextual برای همه توکن‌ها | توکن بعدی (sequence generation)         |






### 🔹 یک دیاگرام ساده ذهنی
        Input: [CLS] The capital of France is [MASK] .
               ↓
        Embedding (Token + Position + Segment)
               ↓
        Encoder Block × N
          ├── Multi-Head Self-Attention (bidirectional)
          ├── Feed Forward
          └── Residual + Norm
               ↓
        Contextualized Representations
               ↓
        Softmax Head (روی [MASK])
               ↓
        Output: "Paris"

---

### ♦️ نحوه استفاده از مدل های MaskedLM برای تسک حدس زدن کلمات حذف شده

         tokenizer = AutoTokenizer.from_pretrained(model_name)
         model = AutoModelForMaskedLM.from_pretrained(model_name) 
        
         nlp_fill = pipeline("fill-mask", model=model, tokenizer=tokenizer)
         results = nlp_fill(text) 
         
         print(f" {r['sequence']} (prob={r['score']:.4f})") 

