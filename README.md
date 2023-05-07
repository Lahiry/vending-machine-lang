# Vending Machine Lang 🥤

## EBNF

```python
VENDING_MACHINE = "Hum, what should I get?",  VENDING_MACHINE_SETUP, "\n", BUY, "\n", "I guess that's enough!"

VENDING_MACHINE_SETUP = DEFINE_CAPACITY, "\n", { DEFINE_ITEM }

DEFINE_CAPACITY = "Vending Machine capacity is", NUMBER, "x", NUMBER, "x", NUMBER

DEFINE_ITEM = POSITION, "is", IDENTIFIER, PRICE, UNITS

VENDING_MACHINE_ACTION = { SELECT_PRODUCT | VERIFY_SELECTED | VERIFY_PRICE | VERIFY_POSITION_ITEM | VERIFY_POSITION_PRICE | VERIFY_POSITION_UNTIS | PAY | CANCEL } 

BUY = VENDING_MACHINE_ACTION | { WHILE | IF }

SELECT_PRODUCT = "Select product", POSITION

SELECT_PAYMENT_METHOD = Select payment method as PAYMENT_METHOD

SELECT_PAYMENT_TYPE = Select payment type as PAYMENT_TYPE

PAYMENT_METHOD = "credit card" | "debit card"

PAYMENT_METHOD = "insert" | "approximation"

CHECK = "Check", "selected items" | "total price" | POSITION, "item" | POSITION, "price" | POSITION, "units"

PAY = "Pay"

CANCEL = "Cancel"

WHILE = "While", "(", CONDITION, ")", "{", "\n", { VENDING_MACHINE_ACTION }, "\n", "}"

IF = "If", "(", CONDITION, ")", "{", "\n", { VENDING_MACHINE_ACTION }, "\n", "}"

CONDITION = { PRICE | "total price" | POSITION, "item" | POSITION, "price" | POSITION, "units", COMPARISON, PRICE | "total price" | POSITION, "item" | POSITION, "price" | POSITION "units" }

COMPARISON = "==", ">", "<", "&&", "||"

POSITION = LETTER, NUMBER 

PRICE = "$", NUMBER

UNITS = NUMBER, "units"

LETTER = ("a" | "b" | "c" | "d" | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n" | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x" | "y" | "z" | "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J" | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T" | "U" | "V" | "W" | "X" | "Y" | "Z")

DIGIT = ("0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9")

NUMBER = DIGIT, { DIGIT }

IDENTIFIER = { LETTER | DIGIT }
```

## Exemplo de uso

```lua
"Hum, what should I get?

Vending machine capacity is 5x10x10 slots
A1 is Light Coke, $5, 3 units
A2 is Snickers, $2, 5 units

Select product A1
Select product A2
while (total price < $10) {
 select product A2
}
Select payment as credit card
Verify selected products
Verify total price
Pay

I guess that's enough!
```
