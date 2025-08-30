
### 📊 تسک‌های قابل انجام با AutoModelForSeq2SeqLM

| #  | 🎯 تسک                                       | 📖 توضیح                                                         | 🤗 مثال مدل                                             |
| -- | -------------------------------------------- | ---------------------------------------------------------------- | ------------------------------------------------------- |
| 1  | **Machine Translation** (ترجمه ماشینی)       | تبدیل متن از زبانی به زبان دیگر                                  | `Helsinki-NLP/opus-mt-en-de`, `facebook/mbart-large-50` |
| 2  | **Text Summarization** (خلاصه‌سازی متن)      | تولید خلاصه فشرده از متن طولانی                                  | `facebook/bart-large-cnn`, `google/pegasus-xsum`        |
| 3  | **Question Answering (Abstractive QA)**      | پاسخ‌گویی تولیدی بر اساس متن                                     | `google/t5-v1_1-base`, `facebook/bart-large`            |
| 4  | **Text Generation (Story/Essay Generation)** | نوشتن متن آزاد مثل داستان و مقاله                                | `t5-base`, `flan-t5-xl`                                 |
| 5  | **Paraphrasing (بازنویسی متن)**              | بازنویسی جمله با همان معنا                                       | `t5-small`, `parrot-paraphraser`                        |
| 6  | **Grammar Correction**                       | اصلاح اشتباهات نگارشی و دستوری                                   | `t5-base`, `flan-t5-base`                               |
| 7  | **Information Extraction**                   | استخراج موجودیت‌ها یا اطلاعات کلیدی از متن                       | `t5-base`                                               |
| 8  | **Code Generation**                          | تولید کد از دستور متنی                                           | `Salesforce/codet5-base`                                |
| 9  | **General Text-to-Text Tasks**               | هر نوع «ورودی متنی → خروجی متنی» (مثلاً ترجمه، طبقه‌بندی به متن) | `t5-base`, `flan-t5`                                    |
| 10 | **Text Infilling / Denoising**               | پرکردن جای خالی در متن ناقص                                      | `facebook/bart-base`                                    |
