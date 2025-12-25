---
---
**all the below was done within a virtualenv environment**; pikepdf is needed as a dependency in ocrmypdf

pip install pikepdf

Collecting pikepdf
  Using cached pikepdf-3.2.0.tar.gz (2.3 MB)
  Installing build dependencies ... done
  Getting requirements to build wheel ... done
  Preparing wheel metadata (pyproject.toml) ... done
Requirement already satisfied: Pillow>=6.0 in c:\\users\\joe\\documents\\projects\\python\\django\\django\_ocr\_backend\\ocr-env\\lib\\site-packages (from pikepdf) (8.3.2)
Collecting lxml>=4.0
  Using cached lxml-4.6.3.tar.gz (3.2 MB)
  Preparing metadata (setup.py) ... done
Using legacy 'setup.py install' for lxml, since package 'wheel' is not installed.
Building wheels for collected packages: pikepdf
  Building wheel for pikepdf (pyproject.toml) ... error
  ERROR: Command errored out with exit status 1:
  command: 'C:\\Users\\Joe\\Documents\\Projects\\Python\\Django\\Django\_OCR\_backend\\ocr-env\\Scripts\\python.exe' 'C:\\Users\\Joe\\Documents\\Projects\\Python\\Django\\Django\_OCR\_backend\\ocr-env\\lib\\site-packages\\pip\\\_vendor\\pep517\\in\_process\\\_in\_process.py' build\_wheel 'C:\\Users\\Joe\\AppData\\Local\\Temp\\tmpfx0fg4fy'
      cwd: C:\\Users\\Joe\\AppData\\Local\\Temp\\pip-install-ke8eqsd5\\pikepdf\_b2e2a57aff1846628db3e5247040ddc8
  Complete output (43 lines):
  running bdist\_wheel
  running build
  running build\_py
  creating build
  creating build\\lib.win-amd64-3.10
  creating build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\codec.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\jbig2.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\objects.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\\_cpphelpers.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\\_methods.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\\_version.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\\_xml.py -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\\_\_init\_\_.py -> build\\lib.win-amd64-3.10\\pikepdf
  creating build\\lib.win-amd64-3.10\\pikepdf\\models
  copying src\\pikepdf\\models\\encryption.py -> build\\lib.win-amd64-3.10\\pikepdf\\models
  copying src\\pikepdf\\models\\image.py -> build\\lib.win-amd64-3.10\\pikepdf\\models
  copying src\\pikepdf\\models\\matrix.py -> build\\lib.win-amd64-3.10\\pikepdf\\models
  copying src\\pikepdf\\models\\metadata.py -> build\\lib.win-amd64-3.10\\pikepdf\\models
  copying src\\pikepdf\\models\\outlines.py -> build\\lib.win-amd64-3.10\\pikepdf\\models
  copying src\\pikepdf\\models\\\_\_init\_\_.py -> build\\lib.win-amd64-3.10\\pikepdf\\models
  running egg\_info
  writing src\\pikepdf.egg-info\\PKG-INFO
  writing dependency\_links to src\\pikepdf.egg-info\\dependency\_links.txt
  writing requirements to src\\pikepdf.egg-info\\requires.txt
  writing top-level names to src\\pikepdf.egg-info\\top\_level.txt
  listing git files failed - pretending there aren't any
  reading manifest file 'src\\pikepdf.egg-info\\SOURCES.txt'
  adding license file 'LICENSE.txt'
  adding license file 'licenses/license.wheel.txt'
  writing manifest file 'src\\pikepdf.egg-info\\SOURCES.txt'
  copying src\\pikepdf\\\_qpdf.pyi -> build\\lib.win-amd64-3.10\\pikepdf
  copying src\\pikepdf\\py.typed -> build\\lib.win-amd64-3.10\\pikepdf
  running build\_ext
  building 'pikepdf.\_qpdf' extension
  creating build\\temp.win-amd64-3.10
  creating build\\temp.win-amd64-3.10\\Release
  creating build\\temp.win-amd64-3.10\\Release\\src
  creating build\\temp.win-amd64-3.10\\Release\\src\\qpdf
  C:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\VC\\Tools\\MSVC\\14.16.27023\\bin\\HostX86\\x64\\cl.exe /c /nologo /Ox /W3 /GL /DNDEBUG /MD -IC:\\Users\\Joe\\AppData\\Local\\Temp\\pip-build-env-gsqrz976\\overlay\\Lib\\site-packages\\pybind11\\include -IC:\\Users\\Joe\\Documents\\Projects\\Python\\Django\\Django\_OCR\_backend\\ocr-env\\include -IC:\\Users\\Joe\\AppData\\Local\\Programs\\Python\\Python310\\include -IC:\\Users\\Joe\\AppData\\Local\\Programs\\Python\\Python310\\Include -IC:\\Program Files (x86)\\Microsoft Visual Studio\\2017\\BuildTools\\VC\\Tools\\MSVC\\14.16.27023\\include -IC:\\Program Files (x86)\\Windows Kits\\10\\include\\10.0.17763.0\\ucrt -IC:\\Program Files (x86)\\Windows Kits\\10\\include\\10.0.17763.0\\shared -IC:\\Program Files (x86)\\Windows Kits\\10\\include\\10.0.17763.0\\um -IC:\\Program Files (x86)\\Windows Kits\\10\\include\\10.0.17763.0\\winrt -IC:\\Program Files (x86)\\Windows Kits\\10\\include\\10.0.17763.0\\cppwinrt /EHsc /Tpsrc/qpdf\\annotation.cpp /Fobuild\\temp.win-amd64-3.10\\Release\\src/qpdf\\annotation.obj /EHsc /bigobj /==std:c++14==
  ==annotation.cpp==
  src/qpdf\\annotation.cpp(9): ==fatal error C1083: Cannot open include file: 'qpdf/Constants.h': No such file or directory==
  error: command 'C:\\\\Program Files (x86)\\\\Microsoft Visual Studio\\\\2017\\\\BuildTools\\\\VC\\\\Tools\\\\MSVC\\\\14.16.27023\\\\bin\\\\HostX86\\\\x64\\\\cl.exe' failed with exit code 2
  ----------------------------------------
  ERROR: Failed building wheel for pikepdf
Failed to build pikepdf
ERROR: Could not build wheels for pikepdf, which is required to install pyproject.toml-based projects
