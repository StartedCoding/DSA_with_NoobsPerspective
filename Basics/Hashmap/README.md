# Hashmap

Let me start with a simple frustration.

Think of a completely normal scenario.

You own a small juice shop 🧃

You maintain a notebook where you record the price of fruits.
```
Apple  -> 100
Banana -> 40
Orange -> 60
Grapes -> 80
```

A customer approaches and asks:

`Bhaiya, What is the price of Grapes?`

What do you do?

You don’t go and search from start:
```
first fruit -> not Grapes

second fruit -> not Grapes

third fruit -> not Grapes

forth fruit -> this is Grapes
```
> You directly jump to Grapes ->  100.

#### Because humans think by names, not by positions.

### Now think like a computer 😐

A computer doesn’t understand:
```
"Apple"

"Banana"

"Orange"

"Grapes"
```
It understands positions.

So internally your data looks lie this:
```
Index 0 -> Apple, 100
Index 1 -> Banana, 40
Index 2 -> Orange, 60
Index 2 -> Grapes, 80
```

Now when the computer hears:

> "Give me Grapes’s price"

It has absolutely no direct clue where Grapes is.

So it does this:
```
1. Check index 0 -> is this Grapes? ❌

2. Check index 1 -> is this Grapes? ❌

3. Check index 2 -> is this Grapes? ❌

4. Check index 3 -> ohh! yes ✅
```
This is called **Searching**.
