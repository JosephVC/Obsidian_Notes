---
---
![[./_resources/Django_tests_produce_RuntimeError.resources/unknown_filename.png]]

in tests.py, change **from .models import Post** to **from ocr.models import Post**

Also, explicitly declare the root directory the **ocr** app is in when filling out **apps.py**

* **![[./_resources/Django_tests_produce_RuntimeError.resources/unknown_filename.1.png]]**
