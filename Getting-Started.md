**Bought KnoXSS, now what:**

I'm assuming you've procured the pro license which costs USD 107 per annum - This seems to be really reasonable since your very first XSS finding using this tool can give you the ROI

If you're still thinking about procuring, first go to [KnoXSS] (https://knoxss.me) and register for a free account.. This will give you an idea of how you can use the online tool which is mostly a **point and click** type

You can try some [sample sites] (http://brutelogic.com.br/knoxss.html) and see whether KnoXSS finds any XSSes there... Once you're satisfied, may be you wanna' get the pro?

Once you've got Pro:

**Testing the Waters:**

1. Go to [KnoXSS] (https://knoxss.me/pro) and login if prompted
2. You can return back to the [test pages] (http://brutelogic.com.br/knoxss.html) to get yourselves acclamatized... This is a work in progress...  
3. Paste the provided sample URLs into the [KnoXSS] (https://knoxss.me/pro) site

**Using the XPI - Firefox Extension**

TBD

**FUQs: (Frequently Unanswered Questions): **

***ONE:*** What should be in "Extra Data" for POST requests

Let's say we want to scan **http://someurl.com** for XSS using [KnoXSS tool] (https://knoxss.me/pro)... Let's say this is a POST request with the following as the full request:
***Start***

POST /app/core.security.login.event HTTP/1.1
Host: someurl.com
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:45.0) Gecko/20100101 Firefox/45.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: https://someurl.com/app/login.jsp?TYPE=33554433&REALMOID=06-00045ffb-9d34-1d53-ba41-024a0a174072&GUID=&SMAUTHREASON=0&METHOD=GET&SMAGENTNAME=-SM-c0YcVaq2Y%2fJgCFwUxzl%2bFjGUYRdw1odmO6FnFo8ALHEWVne0mzqAGJ5gcfrpupN1&TARGET=-SM-https%3a%2f%2fs2b%2esomeurl%2ecom%2fapp%2fcore%2ehomepage%2eshow%2eevent
Cookie: BD1=14846538758084658965091235329142; BD2=14846538758095410991436877103468; javax.servlet.http.Cookie@61466146=""; javax.servlet.http.Cookie@61a661a6=""; JSESSIONID=00012Fj5NP0q15MeH_T179VoQ9o:14bth2u81; WB_LANG=en; ak_bmsc=CA80C1C75F6B260FE672C9CA252C24FB3A1AB98B512B00006FA280585449566C~pl3yxbQlcdDrg0GYKOfEm4TgyyUM9KkeHpL2ktmiK8+6EFPThPTWbf2pQKhSzCZWLO2evhKPTjyfhYjTXddIv+tyUEn1k7Xvab2/yGIeGmBBTB1VCyQ5HjiT17iFebKSQ3nIP8QjWir217JCpydqyP/j3MzuZfChHZ0qqHoF2be8uYdyNRKQEoJ9tWNzwWI1z7B+yF4nEkOXZ9oolI0hCiwaH1/atMeWWYFaCJwvHPrZE=
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
 
_gid=groupkk&_uid=userkk&langid=en

***End***

For the above example, when you click on Extra Data, this is what you need to enter:

POST Data:
_gid=groupkk&_uid=userkk&langid=en
AUTH Data:
The Cookie: and Referer: to be pasted here, so in our case, it will be:
Referer: https://someurl.com/app/login.jsp?TYPE=33554433&REALMOID=06-00045ffb-9d34-1d53-ba41-024a0a174072&GUID=&SMAUTHREASON=0&METHOD=GET&SMAGENTNAME=-SM-c0YcVaq2Y%2fJgCFwUxzl%2bFjGUYRdw1odmO6FnFo8ALHEWVne0mzqAGJ5gcfrpupN1&TARGET=-SM-https%3a%2f%2fs2b%2esomeurl%2ecom%2fapp%2fcore%2ehomepage%2eshow%2eevent
Cookie: BD1=14846538758084658965091235329142; BD2=14846538758095410991436877103468; javax.servlet.http.Cookie@61466146=""; javax.servlet.http.Cookie@61a661a6=""; JSESSIONID=00012Fj5NP0q15MeH_T179VoQ9o:14bth2u81; WB_LANG=en; ak_bmsc=CA80C1C75F6B260FE672C9CA252C24FB3A1AB98B512B00006FA280585449566C~pl3yxbQlcdDrg0GYKOfEm4TgyyUM9KkeHpL2ktmiK8+6EFPThPTWbf2pQKhSzCZWLO2evhKPTjyfhYjTXddIv+tyUEn1k7Xvab2/yGIeGmBBTB1VCyQ5HjiT17iFebKSQ3nIP8QjWir217JCpydqyP/j3MzuZfChHZ0qqHoF2be8uYdyNRKQEoJ9tWNzwWI1z7B+yF4nEkOXZ9oolI0hCiwaH1/atMeWWYFaCJwvHPrZE=

But how do I get the POST request details to paste in Extra Data in the first place?

