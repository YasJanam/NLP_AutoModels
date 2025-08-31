## Files 
#### 🟨 File 1 : General_INFO
اطلاعات کلی مدل facebook/bart-large-cnn
#### 🟨 File 2 : Layers_List
لیست لایه های مدل facebook/bart-large-cnn به همراه اجزای آنها
#### 🟨 File 3 : Summarize_Layers_list 
خلاصه ای از لایه های مدل 
#### 🟨 File 4 : Encoder_Layers
ساختار استک انکودر و لایه های آن
#### 🟨 File 5 : Decoder_Layers
ساختار استک دیکودر و لایه های آن
#### 🟨 File 6 : Structure_Details
ساختار کل مدل facebook/bart-large-cnn به همراه اجزای آن
#### 🟨 File 7 : facebook_bart_large_cnn
فایل کل کد + نمودار مدل و لیست لایه ها با جزییات بیشتر

## facebook/bart-large-cnn
🔵 model-type : __bart__ (encoder-decoder)

🔵 encoder-layers-num : 12 

🔵 decoder-layers-num : 12 

🟩 __bart_models__  :  __encoder_stack__  ➡️ __decoder_stack__ ( + cross-attention )

 نسخه Large: هر کدام از Encoder و Decoder شامل ۱۲ لایه هستند (در نسخه Base، این عدد ۶ لایه است)


#### 🟨 Encoder (رمزگذار)

به‌صورت Bidirectional (دوطرفه) طراحی شده، مشابه BERT.

شامل ۱۲ لایه (Layer) است که هر لایه عملکردهای attention و feed-forward را اجرا می‌کند.

#### 🟨 Decoder (رمزگشا)

عملکرد Autoregressive (خودبازگشتی) دارد، همانند GPT.

هر مرحله خروجی قبلی برای تولید خروجی مرحله بعد مورد استفاده قرار می‌گیرد.

همچنین شامل مکانیسم Cross-Attention است تا اطلاعات رمزگذاری‌شده از Encoder را در تولید استفاده کند.

#### 🟨 کل مدل BART

در پیش‌آموزش از Denoising Autoencoder استفاده می‌شود: متن ورودی به‌شکل تصادفی مخدوش (با حذف، جابجایی جملات، masked tokens و… ) در می‌آید و مدل یاد می‌گیرد آن را بازسازی کند.

---
## ساختار کلی معماری مدل های bart

<img width="715" height="868" alt="image" src="https://github.com/user-attachments/assets/10eec0d9-6a69-424f-a220-674c98629aa9" />

