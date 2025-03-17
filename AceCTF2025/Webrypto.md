## Webrypto -- web



### Question

I think we can all agree that most of us grew up watching the iconic cartoon Tom & Jerry. Every kid would feel that surge of adrenaline during the thrilling chases and chaotic conflicts between the mischievous mouse and the ever-determined cat. The excitement of those scenes—the heart-pounding moments of escape—sometimes felt almost real.

But then, I heard a little rumor: what if all those chases were fake? What if Tom and Jerry were actually friends all along? That revelation shook me. I had no one to ask about this mind-bending twist, so I decided to take matters into my own hands—I created a web app to settle this question once and for all.

I know the truth now. Do you think you can uncover it too?

[](https://chal.acectf.tech/Webrypto/)



### Approach

We visit the website and find the code that returns the flag.

There are 2 parameters to be met to recieve the flag:
1. `tom` and `jerry` shouldn't be the same when passing the request.
2. md5 hash of 'ACECTF`tom`' == 'ACECTF`jery`' (md5 collision attack)

To satisfy these, we modify our url to this `https://chal.acectf.tech/Webrypto/?tom[]=1&jerry[]=2` which prints the flag.

Why?

- Condition 1: When you pass tom[]=1 and jerry[]=2, PHP interprets these as arrays and reads:
  ```
  $_GET['tom'] = [1]
  $_GET['jerry'] = [2]
  ```
  Arrays in PHP are compared by their contents. Since [1] and [2] are different arrays, the condition evaluates to true

- Condition 2: The md5() function in PHP returns NULL when given an array as input. This is because you cannot directly concatenate a string ('ACECTF') with an array.
  Therfor the code is interpreted as:
  ```
  md5('ACECTF' . $_GET['tom']) -> returns NULL.
  md5('ACECTF' . $_GET['jerry']) -> returns NULL.
  ```
  The comparison NULL == NULL evaluates to true

---

### Flag

```
ACECTF{70m_4nd_j3rry_4r3_4ll135}
```