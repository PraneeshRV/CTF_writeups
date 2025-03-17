### Description:

This image looks normal at first, but something important is hidden inside. The secret is carefully concealed, making it hard to find.
Your task is to explore the image, uncover the hidden message, and reveal what’s concealed.
Do you have what it takes to crack the code and unlock the secret?

### Steps :
Use Binwalk to extract files from the png

![alt text](images/image1.png)

Use zip2john to create hash

![alt text](images/image2.png)

use johntheripper to find the password

![alt text](images/image3.png)

extract zip file to get the encrypted flag

![alt text](images/image4.png)

use caesar cipher to decipher the flag

![alt text](images/image5.png)

### Flag

```ACECTF{h4h4_y0u'r3_5m4r7}```