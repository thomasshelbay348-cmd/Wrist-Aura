# Wrist Aura — Firebase Setup

## 1. Firebase Authentication enable karein

Firebase Console mein project `wrist-aura` open karein. **Build > Authentication > Sign-in method** par jaakar **Email/Password** provider enable karein.

Phir **Users** tab mein admin user create karein:

- Email: `wristaura36@gmail.com`
- Password: apna naya strong password use karein. Original HTML mein jo password tha usay reuse na karein kyun ke woh client code mein exposed tha.

Website ke admin lock button par isi email ke user ka password enter hoga.

## 2. Firestore Database

Firebase Console mein **Build > Firestore Database** open karein aur database create karein. Agar database pehle se bana hua hai to dobara create na karein.

Rules tab mein `firestore.rules` file ka complete content paste karke **Publish** karein. Is ruleset mein public visitors products read kar sakte hain, lekin create/edit/delete sirf authenticated admin email kar sakta hai.

## 3. Website files

`index.html` aur `firestore.rules` ko apni hosting ke saath upload karein. `index.html` mein Firebase project configuration pehle se `wrist-aura` project ki lagi hui hai.

## 4. First run aur migration

Agar Firestore ka `products` collection empty hai, website pehle local/default products ka preview dikhayegi. Admin account se unlock karne ke baad ye products Firestore mein ek dafa migrate ho jayenge.

Agar aapke Firestore collection mein pehle se products hain, website unhi ko use karegi aur local data ko ignore karegi.

## 5. Test

Ek device par admin login karke product add, edit, ya delete karein. Doosri device par website khol kar check karein. Realtime listener ki wajah se page refresh ke baghair bhi catalog update hona chahiye. Agar update na aaye to dono devices internet par hon aur Firestore Rules published hon.

## Important security note

Firebase web configuration values browser mein hona normal hai; security Rules aur Firebase Authentication asal protection provide karte hain. Client-side hard-coded admin password remove kar diya gaya hai. `firestore.rules` publish kiye baghair add/edit/delete operations permission error denge.
