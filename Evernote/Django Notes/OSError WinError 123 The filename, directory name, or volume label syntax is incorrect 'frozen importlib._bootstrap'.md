---
---
I ran into this error after re-cloning my tutorial\_backend2 project to my desktop (the laptop's repo was changed from 'master' to 'main' but the desktop didn't see this, and i didn't want to screw up the overall repo by changing things again on the desktop) 

After trying to run the server in a freshly-cloned repo, I ran into the below error

![[./_resources/OSError_WinError_123_The_filename,_directory_name,_or_volume_label_syntax_is_incorrect_'frozen_importlib._bootstrap'.resources/unknown_filename.png]]
 (the above is only a snippet of the error, but wanted some other context in addition to the main OSError)

I read that a potential fix was to run **migrate**, but that lead to **ModuleNotFoundError: No module named 'admin\_honeypot'**

OK, so now try to uninstall/re-install the above package

That lead to Poetry trying to update the current packages, leading to a needed update to the cryptography package in python (which itself had just been updated with Rust).  

**The fix to this was to update pip itself - BOTH WITHIN YOUR POETRY SHELL AND REGULAR ENVIRONMENT - which allowed an overall update to Poetry and the project requirements.**
