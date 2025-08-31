# facebook/bart-large-cnn
🔵 model-type : __bart__ (encoder-decoder)

🔴 encoder-layers-num : 12 

🟡 decoder-layers-num : 12 

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
