## Fall of 2022 -- OSINT


### Challenge

It was a peaceful time — schools were over, college admissions were delayed, and COVID was slowly on the decline. It seemed like the perfect time to relax and check my phone for her txts.

The funny thing is, I never got any. So I considered it just another gloomy year.

Anyways, here’s the domain for this CTF: [acectf.tech](https://acectf.tech/)

What? You already knew this domain? Oh, I guess you’ll have no trouble finding the flag then.

Good Luck!

### Solution

From the hint that is given, it must be something related to .txt files. So I used the most basic tool to search for any .txt files in the website

`dig acectf.tech TXT`

The command directly prints the TXT file which has the flag as its name.


### Flag

```
ACECTF{y0u_g07_7h3_73x7}