Firstly we need a way to create a bunch of accounts to test on as with any platform, let's get to it


https://lichess.org/signup

So there are two main security features with lichess registration 

1.  hCaptcha 
-Methinks this isn't going to do much

2.  Whitelist of email providers
- This is more tricky

2 Is more tricky because we need to create N email accounts to bypass the registration but maybe we can find a weak one or one that supports making many accounts (we gonn need a few)

Ideally we want at worst an email provider with a captcha that doesn't require a phone number, you know let's see if there's another way to do this

Luckily lichess isn't corrupted at this level and so their whitelist is open source.  This allows us to be much less nasty!  Thank goodness!

https://github.com/lichess-org/lila/blob/18a1e7196f888a5e3b5994e8750a45a4234a5e66/modules/security/src/main/DisposableEmailDomain.scala 

It can be found here
Unfortunately we'd prefer no phone verification but I think we're going to have to bypass that, that's ok.

Some require money e.g. hushmail
https://www.zoho.com/signup.html is interesting because it requires an email to sign up?  So can we use an insecure email provider and do that?
So zoho has some whitelist filtering, let's come back to it hush would also be an option with a company email
Ok let's look at sms verification services and see if any are free or very cheap for our cheating purposes

I'm not going to go too much into sms verification sufficieth to say

If you need phone numbers and you want to do it yourself you need a trunk line.


Then you need to automate registration against an email provider.

I'll look for that publicly or implement my own privately (I'm sure it's public though)

Once you have some numbers you can automate creating a bunch of emails 1 number = like 100 emails so yeah it scales pretty hard.

Let's start with this

https://github.com/Skuxblan/Outlook-account-creator

So we'll need to provision let's say 20 accounts first.

I'll write the code later and add the hcaptcha bypass tomorrow 

So what we'll document here is bypassing lichess registration security given an email that falls within their whitelist domain

As a note I know from experience lichess is very very bad about ip regulation which isg ood for vpn use but it also means, 1 ip -> 100s of lichess accounts != ban

So once we move from registration we will write a bot to just play games at a level that will be the largest part of the work the rest will be scaling that bot into higher and higher ratings in time frames that aren't detectable

Since lichess supports strong players making new accounts, we can just make a bunch of new accounts which are super strong, this will make bot moves harder to detect (I think) 

provided we handle the rest of the signal but we could also create a varitey of accounts, let's start at 2000 for simplicity