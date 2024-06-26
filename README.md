# Втора лабораториска вежба по Софтверско инженерство
## Гоце Дамњановски, бр. на индекс: 203155
### Control Flow Graph
![SI_Lab2_CFG](https://github.com/goce-damnjanovski/SI_2024_lab2_203155/assets/25536314/cdaf87cf-f890-4b4e-9a56-976001b94864)

### Цикломатска комплексност
Цикломатската комплексност на кодот е 10. Резултатот е добиен преку сите три начини.
1. Според бројот на региони: Постојат 10 региони, па оттука цикломатската комплексност изнесува 10.
2. Според разликата на ребрата и јазлите: Од формулата CC = E - N + 2, каде E = број на ребра, N = број на јазли следува:
Е = 35; N = 27; следува: CC = 35 - 27 + 2 = 10
3. Според бројот на предикатни јазли: Од формулата CC = P + 1, каде P е бројот на предикатни јазли следува:
P = 9; следува: CC = 9 + 1 = 10

### Тест случаи според критериумот Every Branch
![EveryBranch](https://github.com/goce-damnjanovski/SI_2024_lab2_203155/assets/25536314/f06d1f05-a0f2-4628-9d36-ae8edeef9d26)
Со тест случајот: allItems == null го опфаќаме случајот кога листата е празна. Во тој случај треба да биде фрлен исклучок.

Со тест случајот: items = {["SomeItem", 0123, 350, 1.2], [null, 1234, 300, 0.5], ["", 2345, 200, 0]}, payment = 1500,
се опфатени случаи кога е креирана листа со елементи и притоа се опфатени случаи кога:
1. Производот има назив, има регуларен баркод, има попуст и цената е поголема од 300: ["SomeItem", 0123, 350, 1.2]
2. Називот e null, има регуларен баркод, има попуст и цената е еднаква на 300: [null, 1234, 300, 0.5]
3. Производот нема назив, има регуларен баркод, нема попуст и цената е помала од 300: ["", 2345, 200, 0]
Исто така опфатен е случајот кога вкупната сума има помала вредност од вредноста на payment.

Тест случајот: items = {["SomeItem", 0123, 350, 1.2], [null, 1234, 300, 0.5], ["", 2345, 200, 0]}, payment = 300,
ги има истите вредности како и претходниот случај со таа разлика што во овој случај е опфатена состојбата кога вкупната сума има поголема вредност од вредноста на payment.

Тест случајот: items = {["SomeItem", null, 350, 1.2]}, payment = anything; го опфаќа случајот кога вредноста на баркодот е null. Во овој случај треба да биде фрлен исклучок.

Тест случајот: items = {["SomeItem", #!%&@, 350, 1.2]}, payment = anything ; го опфаќа случајот кога имаме недозволени карактери како вредност на баркодот. Во овој случај треба да биде фрлен исклучок.

### Тест случаи според критериумот Multiple Condition
![MultipleCondition](https://github.com/goce-damnjanovski/SI_2024_lab2_203155/assets/25536314/bfc8c945-d87d-4694-be10-44ed920e21a2)

Со Multiple Condition го тестираме условот (item.getPrice() > 300 && item.getDiscount() > 0 && item.getBarcode().charAt(0) == '0'). Со тестирање ги имаме опфатено следниве случаи:
1. ТТТ: сите три подуслови треба да бидат точни односно item.getPrice() > 300, item.getDiscount() > 0, item.getBarcode().charAt(0) == '0' треба да вратат TRUE. Тоа го добиваме со случајот:
item = ["SomeItem", 0123, 500, 1.2], каде item.getPrice() = 500, item.getDiscount() = 1.2, item.getBarcode().charAt(0) = '0'.
2. ТТF: првите два подуслови треба да бидат точни, а третиот да не е точен односно item.getPrice() > 300, item.getDiscount() > 0 треба да вратат TRUE, а item.getBarcode().charAt(0) == '0' треба да врати FALSE.
Тоа го добиваме со случајот: item = ["SomeItem", 1234, 500, 1.2], каде item.getPrice() = 500, item.getDiscount() = 1.2, item.getBarcode().charAt(0) = '1'.
3. ТFX: првиот подуслов треба да биде точен, вториот да не е точен и вредноста на третиот не е важна за условот односно item.getPrice() > 300 треба да врати TRUE, item.getDiscount() > 0 треба да врати FALSE.
Тоа го добиваме со случајот: item = ["SomeItem", 0123, 500, 0], каде item.getPrice() = 500, item.getDiscount() = 0.
4. FXX: првиот подуслов треба да да не е точен, а вредноста на вториот и третиот не е важна за условот односно item.getPrice() > 300 треба да врати FALSE.
Тоа го добиваме со случајот: item = ["SomeItem", 0123, 200, 1.2], каде item.getPrice() = 200.
