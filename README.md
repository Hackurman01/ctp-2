# CTP-2

## Reversing
###  **Challenge** - keygenme-py
We are given a "keygenme-trial.py" python file. Upon opening we see that it is a code for a software named "Arcane Calculator."

Now this software is a trial version which gives us trial featues and additional features that can be accessed upon entering the license key. In general ctf fashion, this license key will be our flag.
![Capture](https://github.com/Hackurman01/ctp-2/assets/144946633/294e7d31-f268-4358-804b-8b871de42f76)


Now the key is broken into 3 formats: 2 static part and a dynamic part which will be of 8 characters as denoted by the "xxxxxxxx".

So looking upon the topic of interest ie. the check_key function, it:
* First: Takes the input key and checks its length with the full key template format: 
    ``` python
    key_part_static1_trial = "picoCTF{1n_7h3_|<3y_of_"
    key_part_dynamic1_trial = "xxxxxxxx"
    key_part_static2_trial = "}"
    key_full_template_trial = key_part_static1_trial + key_part_dynamic1_trial + key_part_static2_trial
    ```

    ...which will deny us access straightaway upon failure.
* Second: It checks the first static part of the key with the template :"picoCTF{1n_7h3_|<3y_of_". So all static 1st part of the key must match. 

  The checking and verification part is being done by traversing on the characters of input key which after checking the first static part puts the traversing element 'i' to check on the dynamic part.
* Lastly: It checks the dynamic part of the key which is checked via a specified 'rule'(the comparison not being direct and also being in a particular unique sequence) by comparing characters of the input key with the username_trial string. The character of the user_key is checked with the characters of the username_trial key which is first put through SHA(Secure Hash Algorithm)-256 encryption function using the hashlib module then put through a hexdigest(). 

    For example: 
    ```Python
    if key[i] != hashlib.sha256(username_trial).hexdigest()[2]:
            return False
        else:
            i += 1
    ```
    In this line the particular key character(5th dynamic character) is checked with the 2nd index(ie the 3rd positioned) character of the hexadecimal converted sha256 hash of the username_trial. 

    Finally if all the characters are verified then the function returns True to the enter_lincense() fucntions which in turn envokes the :         decrypt_full_version(user_key) function.

Therefore we must extract the required characters and concat them up with the static parts of the key to get the flag. The code for which would be:
```Python
import hashlib
key_part_static1 = "picoCTF{1n_7h3_|<3y_of_"
key_part_static2 = "}"
username_trial = b"MORTON"
hashed= hashlib.sha256(username_trial).hexdigest()
key_part_dynamic1=hashed[4]+hashed[5]+hashed[3]+hashed[6]+hashed[2]+hashed[7]+hashed[1]+hashed[8]
key_full = key_part_static1 + key_part_dynamic1 + key_part_static2
print(key_full)
```


###### TODO : test performance on toolbox container"???
