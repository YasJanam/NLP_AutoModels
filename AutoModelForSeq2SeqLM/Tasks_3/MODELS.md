

### MODELS 

| 🏷️ مدل          | ⚙️ معماری       | 🎯 کاربرد اصلی                                                          | ➕ کاربردهای فرعی                             | 🤗 مثال مدل‌ها                                                                   |
| ---------------- | --------------- | ----------------------------------------------------------------------- | -------------------------------------------- | -------------------------------------------------------------------------------- |
| **T5 / Flan-T5** | Encoder–Decoder | ✅ همه‌کاره (Summarization, Translation, QA, Paraphrasing, Data-to-Text) | General text generation, Style transfer      | `t5-small`, `t5-base`, `google/flan-t5-xl`                                       |
| **BART**         | Encoder–Decoder | ✅ Summarization (خبر، مقاله)                                            | QA, Dialogue generation, Paraphrasing        | `facebook/bart-base`, `facebook/bart-large-cnn`                                  |
| **Pegasus**      | Encoder–Decoder | ✅ Summarization حرفه‌ای (long docs, news, scientific)                   | Abstractive QA                               | `google/pegasus-xsum`, `google/pegasus-cnn_dailymail`                            |
| **mBART**        | Encoder–Decoder | ✅ Translation چندزبانه                                                  | Multilingual summarization, cross-lingual QA | `facebook/mbart-large-50`, `facebook/mbart-large-cc25`                           |
| **MarianMT**     | Encoder–Decoder | ✅ Translation (جفت‌زبان مشخص)                                           | — (فقط ترجمه)                                | `Helsinki-NLP/opus-mt-en-fr`, `Helsinki-NLP/opus-mt-en-de`                       |
| **ProphetNet**   | Encoder–Decoder | ✅ Summarization                                                         | Paraphrasing, Conditional generation         | `microsoft/prophetnet-large-uncased`, `microsoft/prophetnet-large-uncased-squad` |


---

###✅ خلاصه‌ی ساده:

🔵 **T5** → همه‌ فن‌ حریف (هر چی text-to-text)

🟢 **BART** → خلاصه‌ سازی + QA + دیالوگ

🔴 **Pegasus** → خلاصه‌ سازی حرفه‌ای

🟣 **mBART** → خلاصه‌ سازی و ترجمه چند زبانه

🟡 **MarianMT** → فقط ترجمه

🟠 **ProphetNet** → خلاق تر generation ولی برای BART شبیه 
