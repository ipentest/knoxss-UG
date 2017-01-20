# knoxss-UG
Documentation for knoXSS tool by @brutelogic

**Bought KnoXSS, Now What:**

I'm assuming you've procured the pro license which costs USD 107 per annum - This seems to be really reasonable since your very first XSS finding using this tool can give you the ROI

If you're still thinking about procuring, first go to [KnoXSS] (https://knoxss.me) and register for a free account.. This will give you an idea of how you can use the online tool which is mostly a **point and click** type

You can try some [sample sites] (http://brutelogic.com.br/knoxss.html) and see whether KnoXSS finds any XSSes there... Once you're satisfied, may be you wanna' get the pro?


Once you've got Pro:

**Testing the Waters:**

1. Go to [KnoXSS] (https://knoxss.me/pro) and login if prompted
2. You can return back to the [test pages] (http://brutelogic.com.br/knoxss.html) to get yourselves acclamatized... Please be aware that the [test pages] (http://brutelogic.com.br/knoxss.html) are a work in progress...  
3. Paste the provided sample URLs into the [KnoXSS] (https://knoxss.me/pro) site

**Using the XPI - Firefox Extension**

TBD



**FUQs: (Frequently Unanswered Questions): **

***ONE:*** What should be in "Extra Data" for POST requests or How to handle POST requests?

Let's say we want to scan **http://someurl.com** for XSS using [KnoXSS tool] (https://knoxss.me/pro)... Let's say this is a POST request with the following as the full request:

***Start***

```
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
```
***End***

For the above example, when I click on the *Extra Data* button, this is what I would need to paste:

***POST Data:***

```
_gid=groupkk&_uid=userkk&langid=en
```
***AUTH Data:***
The ***Cookie: and Referer: headers*** to be pasted here, so in our case, it will be:
```
Referer: https://someurl.com/app/login.jsp?TYPE=33554433&REALMOID=06-00045ffb-9d34-1d53-ba41-024a0a174072&GUID=&SMAUTHREASON=0&METHOD=GET&SMAGENTNAME=-SM-c0YcVaq2Y%2fJgCFwUxzl%2bFjGUYRdw1odmO6FnFo8ALHEWVne0mzqAGJ5gcfrpupN1&TARGET=-SM-https%3a%2f%2fs2b%2esomeurl%2ecom%2fapp%2fcore%2ehomepage%2eshow%2eevent
Cookie: BD1=14846538758084658965091235329142; BD2=14846538758095410991436877103468; javax.servlet.http.Cookie@61466146=""; javax.servlet.http.Cookie@61a661a6=""; JSESSIONID=00012Fj5NP0q15MeH_T179VoQ9o:14bth2u81; WB_LANG=en; ak_bmsc=CA80C1C75F6B260FE672C9CA252C24FB3A1AB98B512B00006FA280585449566C~pl3yxbQlcdDrg0GYKOfEm4TgyyUM9KkeHpL2ktmiK8+6EFPThPTWbf2pQKhSzCZWLO2evhKPTjyfhYjTXddIv+tyUEn1k7Xvab2/yGIeGmBBTB1VCyQ5HjiT17iFebKSQ3nIP8QjWir217JCpydqyP/j3MzuZfChHZ0qqHoF2be8uYdyNRKQEoJ9tWNzwWI1z7B+yF4nEkOXZ9oolI0hCiwaH1/atMeWWYFaCJwvHPrZE=
```
* If in doubt, paste the entire HTTP header into the AUTH Data field and check again

* I personally feel that this window needs to be closed with a Save button rather than just clicking on the X at the top... However, please note clicking on the X does make the pasted values remain persistent

***TWO:*** But how do I capture the POST request to paste into *Extra Data* fields, in the first place?

Easiest way is to use any interception proxy such as [Burp Suite] (https://portswigger.net/burp/download.html) or [Fiddler] (https://www.telerik.com/download/fiddler), intercept the request and paste that data into the fields

***THREE:*** Is there some way to know how many requests are being made by ***KnoXSS Pro***? I dont see any log, hence the question - this is especially important when the result says no XSS found

Tool author @brutelogic's comment: A log feature is being implemented, it will not contain this info in the first release but will come in future developments. To be sure there's no XSS, you can check target manually 

You can always see the requests with burp or which ever proxy you use this is handy to see what response knoxss has provided.

***FOUR:*** What happens when the number of users performing the scans go up?

Server will hang if the CPU reaches 100% for sustained periods (several seconds). Currently it doesn't pass 30% even with the heaviest concurrent load. 

***FIVE:*** When I asked @brutelogic " I tried using KnoXSS on some of the sites which have been shown as vulnerable on the [Open Bug Bounty] (https://openbugbounty.org) site, but Knoxss was unable to detect them... So want to know what mistake I was doing

Please ask @RandomRobbie, several of his findings with KNOXSS ended up as submissions there. You might be doing something wrong, KNOXSS can find almost all the simple cases featuring in openbubounty.org

Always check the full paremeters have been sent via knoxss plugin if not re test the site and ensure you provide knoxss with the cookies and the CRSF tokens if there are any.

**Will ask @RandomRobbie and add the answers here**

***SIX:*** You say there's some challenge the author of KnoXSS is facing with the Firefox Add-on (the XPI file)... If everything is working fine in Pro version shouldn't it also work the same on the XPI?

Tool author @brutelogic's concern: The Add-on is currently facing several implementation challenges due to Mozilla's API. Even if using the Add-on to just send targets to KNOXSS to test them, it's advised to (re)test using the main interface. 

This git is a work in progress and things will keep changing with the tool's maturity... So dont forget to Star and Watch

