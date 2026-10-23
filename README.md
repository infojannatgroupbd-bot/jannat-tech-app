# Jannat Tech App (Android + iOS) — jannattechbd.com

একই প্রজেক্ট থেকে দুটো অ্যাপ হয় (Capacitor)। অ্যাপ খুললে লোগো-স্ক্রিন → আপনার সাইট। ইন্টারনেট না থাকলে "আবার চেষ্টা করুন" স্ক্রিন।
App ID: com.jannattechbd.app

## বিল্ড (নিজের কম্পিউটারে কিছু ইনস্টল ছাড়াই, GitHub-এ ফ্রি)
1. GitHub-এ একটি Private repo খুলে এই ফোল্ডারের সব ফাইল আপলোড করুন (.github ফোল্ডারসহ)।
2. Actions ট্যাব → "Android build" → Run workflow। শেষে Artifacts থেকে `jannat-debug-apk` নামিয়ে ফোনে ইনস্টল করে দেখুন।
3. Play Store-এর জন্য signed AAB: একবার keystore বানান (`keytool -genkey -v -keystore release.jks -alias jannat -keyalg RSA -keysize 2048 -validity 10000`), তারপর repo Settings → Secrets-এ দিন:
   ANDROID_KEYSTORE_B64 (`base64 release.jks`), ANDROID_KEYSTORE_PASSWORD, ANDROID_KEY_ALIAS, ANDROID_KEY_PASSWORD। আবার Run করলে `jannat-release-aab` পাবেন। keystore হারাবেন না।
4. iOS: "iOS build" workflow প্রজেক্ট তৈরি ও কম্পাইল চেক করে। App Store-এ পাঠাতে Mac + Xcode (বা Codemagic) লাগে: ios প্রজেক্ট খুলে Team/Signing দিয়ে Product → Archive → Distribute।

## স্টোর অ্যাকাউন্ট (এটি ফ্রি নয়)
- Google Play Console: একবার US$25। Apple Developer Program: বছরে US$99। এটা স্টোরের ফি, অ্যাপ বানানোর খরচ নয়।

## স্টোরে লাগবে
- Privacy Policy পেজ (সাইটে /privacy-policy/), অ্যাপের স্ক্রিনশট, 512px আইকন (play-store-icon-512.png — তৈরি করাই আছে), ফিচার গ্রাফিক।
- অ্যাকাউন্ট খোলার সুবিধা আছে, তাই Play ও Apple দুই জায়গায়ই "অ্যাকাউন্ট ডিলিট" করার উপায় (সাইটে লিংক/ইমেইল) দেখাতে হবে।
- Apple কখনো "শুধু ওয়েবসাইটের র‍্যাপার" বলে রিজেক্ট করে (গাইডলাইন 4.2)। রিভিউ নোটে লিখুন: অর্ডার, ট্র্যাকিং, পেমেন্ট, লগইন ও PC Builder আছে। রিজেক্ট হলে নেটিভ ফিচার (পুশ নোটিফিকেশন, ইত্যাদি) যোগ করতে হবে।
