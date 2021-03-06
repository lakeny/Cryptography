## 1. Meet-in-the-middle შეტევა დისკრეტულ ლოგარითმზე

ვითვლით დისკრეტული ლოგარითმს Zp*-ში, სადაც p არის მარტივი რიცხვი. გვაქვს ოთხი არგუმენტი:

p - მარტივი რიცხვი
g - Zp*-ს გენერატორი
h - Zp*-ს ერთ-ერთი ელემენტი. ცხადია, h = gx (mod p) 
max_x - x-ის მაქსიმალური მნიშვნელობა

ვპოულობთ ისეთ x-ს, რომლისთვისაც სრულდება ტოლობა h = gx (mod p) .

ჩვენ ვუშვებთ რომ max_x არ აღემატება 240-ს.
ტრივიალური ალგორითმით (x-ის ყველა შესაძლო მნიშვნელობისთვის გადაყოლით) მოგვიწევდა 240 გამრავლების ჩატარება. 
მაგრამ ამ შემთხვევისთვის გამოვიყენებთ უფრო სწრაფ შეტევას - meet-in-the-middle attack-ს.

გასაშვებად:
```
python dlog.py
```
stdout-ზე უნდა გამოიტანოთ x-ის მნიშვნელობა. 

## 2. RSA-ზე დაფუძნებული ხელმოწერის გაყალბება
63-ბაიტინი შეტყობინებებისთვის ხელმოწერის დასაგენერირებლად იყენებენ შემდეგ სქემას: საჯარო გასაღები არის RSA-ის სტანდარტული წყვილი (N,e), საიდუმლო გასაღები კი, ასევე სტანდარტულად - (N,d), სადაც N არის 128-ბაიტიანი (1024-ბიტიანი) მთელი რიცხვი. 63-ბაიტიანი შეტყობინება m-ის ხელმოწერა კი გამოითვლება ასე: s = Md(mod N), სადაც:

M = 0x00 m 0x00 m
(დარწმუნდით, რომ M-ის ზომა 128 ბაიტია).

თუკი m-ის ზომა ნაკლებია 63 ბაიტზე, მაშინ შეტყობინებას წინ ემატება 0-ები საჭირო ზომამდე შესავსებად.

ჩვენ ვცდილობთ ვიპოვოთ ხელმოწერა 63-ბაიტიანი challenge შეტყობინებისთვის:

Crypto is hard --- even schemes that look complex can be broken

გვაქვს წვდომა სერვერთან, რომელიც გვიბრუნებს ნებისმიერი 63-ბაიტიანი ან უფრო მოკლე შეტყობინების ხელმოწერას, გარდა challenge შეტყობინებისა.

ასევე, გვაქვს წვდომა ვერიფიკაციის სერვერთან, რომელიც მიიღებს შეტყობინებისა და ხელმოწერის წყვილს და გიპასუხებთ, შეესაბამება თუ არა ხელმოწერა შეტყობინებას.

გასაშვებად:
```
python sign.py
```
და გამოიტანს stdout-ზე challenge შეტყობინების ხელმოწერას.
