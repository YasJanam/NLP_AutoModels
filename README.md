# NLP_AutoModels

---
### AutoModel-Types

| AutoModel-Type                         | Model-Type                | کاربرد کلی           | Trainer        | Task                                                   | Models                                              |
| -------------------------------------- | ------------------------- | -------------------- | -------------- | ------------------------------------------------------ | --------------------------------------------------- |
| **AutoModelForSequenceClassification** | 🔵 Encoder-Only (BERT-like)  |  درک متن   | Trainer        | طبقه‌بندی متن (sentiment analysis، موضوع‌یابی)         | Encoder Models (BERT, RoBERTa, DistilBERT, Electra) |
| **AutoModelForTokenClassification**    | 🔵 Encoder-Only (BERT-like)  |  درک متن   | Trainer        | برچسب‌زنی توکن‌ها (NER، POS tagging)                   | BERT, RoBERTa, XLM-R                                |
| **AutoModelForQuestionAnswering**      | 🔵 Encoder-Only (BERT-like)  |  درک متن   | Trainer        | پرسش‌پاسخ استخراجی (جواب از دل متن)                    | BERT, RoBERTa, DistilBERT, ALBERT                   |
| **AutoModelForMaskedLM**               | 🔵 Encoder-Only (BERT-like)  |  درک متن   | Trainer        | زبان‌مدل‌سازی پوشیده (پرکردن جاهای خالی)               | BERT, RoBERTa, DistilBERT                           |
| **AutoModelForCausalLM**               | 🔴 **Decoder-Only** (GPT-like)   |  **تولید متن** | Trainer        | تولید متن به سبک GPT (زبان‌مدل‌سازی علی)               | GPT-2, GPT-Neo, GPT-J, LLaMA, Falcon                |
| **AutoModelForSeq2SeqLM**              | 🟢 **Encoder-Decoder** (Seq2Seq) | **بازنویسی متن**        | **Seq2SeqTrainer** | مدل‌های Encoder-Decoder (ترجمه، خلاصه‌سازی، تولید متن) | T5, BART, mBART, MarianMT, Pegasus                  |


---

| معماری                        | مثال‌ها                     | نگاه به متن                         | کاربرد اصلی                                     |
| ----------------------------- | --------------------------- | ----------------------------------- | ----------------------------------------------- |
| **Encoder-only**              | BERT, RoBERTa               | کل متن (دوطرفه، bidirectional)      | درک متن (classification, NER, QA extractive)    |
| **Decoder-only (CausalLM)**   | GPT-2, GPT-3, LLaMA, Falcon | فقط گذشته (چپ به راست)              | تولید متن (text generation, completion)         |
| **Encoder-Decoder (Seq2Seq)** | T5, BART, MarianMT, Pegasus | Encoder → کل متن   / Decoder → causal | بازنویسی متن (translation, summarization, etc.) |

---
