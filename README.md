# parsi.io

## Address extractor

### Supported marker
- Address, Email, URL, Phone Number extractor

### Example
```python
from parsi_io.modules.address_extractions import AddressExtraction
extractor = AddressExtraction()
extractor.run('آدرس خیابان شهیدبهشتی می‌باشد و برای اطلاعات بیشتر به page.com مراجعه فرمایید')
```
### Output
```
{'address': ['آدرس خیابان شهیدبهشتی'], 'email': [], 'url': ['page.com'], 'number': [], 'address_span': [0, 21], 'email_span': [], 'url_span': [54, 62], 'number_span': []}
```

## Cause and Effect extractor
- Determines whether a sentence is causal

### Supported marker
- Causal marker extarctor

### Example
```python
from parsi_io.modules.cause_effect_extractions import 
extractor = CauseEffectExtraction()
extractor.run('چون نمی‌خواستم اون چیزی از ماجرا بفهمه، مجبور به تظاهر شدم.')
```
### Output
```
{
      "flag": "بله",
      "marker": "چون",
      "marker_span": "[0, 3]"
    }
```

## Quranic extractor
- Extracts parts (at least two words) of The Holy Quran
 verses with their surah and verse number from input text

### Supported marker
- The Holy Quran verses extractor

### Example
```python
from parsi_io.modules.quranic_extractions import QuranicExtraction
extractor = QuranicExtraction(model = 'exact', precompiled_patterns='prebuilt')
extractor.run('شان نزول آیه ی انما وليكم اللّه ورسوله والّذين امنوا')
```
### Output
```
{
    'input_span': [15, 52],
    'extracted': 'انما وليكم اللّه ورسوله والّذين امنوا',
    'quran_id': '5##55',
    'verse': 'إِنَّمَا وَلِيُّكُمُ اللَّهُ وَ رَسُولُهُ وَ الَّذِينَ آمَنُوا الَّذِينَ يُقِيمُونَ الصَّلَاةَ وَ يُؤْتُونَ الزَّكَاةَ وَ هُمْ رَاكِعُونَ'
}
```

## TimeDate extractor
- Extracts Time Date Markers (stable)
- Extract Values (Unstable)

### Supported marker
- All Time and Date Markers

### Example
```python
from parsi_io.modules.time_extractions import TimeExtraction
extractor = TimeExtraction()
extractor.run("ماریا شنبه عصر در ساعت نه و پنجاه نه دقیقه - مورخ 13 می 1999 با نادیا تماس گرفت اما نادیا بعدا در 1100/09/09 قمری به پرسش او پاسخ داد.")
```
### Output
```
{
    'Normalized_Sentence': 'ماریا شنبه عصر در ساعت نه و پنجاه نه دقیقه - مورخ 13 می 1999 با نادیا تماس گرفت اما نادیا بعدا در 1100/09/09 قمری به پرسش او پاسخ داد.',
    'Spans': [(6, 15), (18, 43), (45, 61), (98, 114)],
    'Markers': ['شنبه عصر ', 'ساعت نه و پنجاه نه دقیقه ', 'مورخ 13 می 1999 ', '1100/09/09 قمری '],
    'Values': ['شنبه عصر', '09:59:00', '13/05/1999', '1100/09/09 ه.ق']
}
```


## Test
Add test cases to parsi_io/test/testcases/\[marker_name].json in the following template

### Template
```
[
    {
        "id":test ID,
        "input":input text,
        "outputs":output dictionary
    },
    ...
]
```

## Contributors
| Marker      | Contributors |
| ----------- | ----------- |
| Address Extraction      | Amirreza Mozayani, Arya Kosari, Seyyed Mohammadjavad Feyzabadi, Omid Ghahroodi       |
| CauseEffect Extraction      | Rozhan Ahmadi, Mohammad Azizmalayeri, Mohammadreza Fereiduni, Saeed Hematian, Seyyed Ali Marashian, Maryam Gheysari       |
| Number Extraction   | Mohammad Ali Sadraei Javaheri, Mohammad Mozafari        |
| Quranic Extraction    | Seyyed Mohammad Aref Jahanmir, Alireza Sahebi, Ali Safarpoor Dehkordi, Mohammad Mehdi Hemmatyar, Morteza Abolghasemi, Saman Hadian      | 
| Time Date Extraction    |  | 
