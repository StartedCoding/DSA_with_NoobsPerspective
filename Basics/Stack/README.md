# Stack

## So, first of all... WHY do we even need a Stack?

Let me ask you something.
```
You are coding.
You mess up.
You press Ctrl + Z.
```
> What should undo first?

- Not something you did 10 minutes ago.
- Not something random.

👉 The last thing you did.

That’s it. That’s why the Stack exists.

That pattern - `the last thing should be handled first` - shows up everywhere, not just in code.
```
1. We stack plates in the kitchen.
2. We don’t pull one out from the middle.
3. We take the top plate first.
```

Some problems just say:

`Handle the latest thing first. No arguments.`

That’s where Stack comes in.

## Okay, so WHAT exactly is a Stack?
Let’s not rush into definitions.
A Stack is not anything **fancy**.

It follows a descipline:
> You can put things only at one end

> You can take things only from the same end

That end is called the top.

That’s it.
No side doors.
No shortcuts.

If you attempt to grab something from the middle, Stack just responds with:
'No. That’s not how this works.'

This hard-and-fast rule has a special name:

> Last In, First Out (LIFO)

Whatever goes in last...
comes out first.

## Why is Stack so strict?

Because of strictness, life becomes easier.

What if plates could be pulled from anywhere?
```
Plates are broken

Order is broken

Our logic is broken
```
Stack give us fewer options, but It gives us peace.

And honestly?
That’s why it works so well.


## Where does this discipline feel natural?
You have already seen Stack in action.

### 1. Undo / Redo

The last action is the first one to undo.

Anything else would feel wrong.

You type:
```
a
ab>
abc
```
Now you press Ctrl + Z once.

What should happen?
```
abc → ab
```

Not a.
Not an empty string.

The last change is undone first.

That’s Stack.

### 2. Brackets like ( { [ ] } )

The last opening bracket must close first.

Otherwise, the structure breaks.

Consider this expression:
```
( { [ ] } )
```

The order of opening is:
```
( -> { -> [
```
This means that the closing order must be:
```
] -> } -> )
```

But if you attempt this instead:
```
( { [ } ] )
```

It will fail right away.

Why?

Because the last opened bracket must be the first to close.

This is what Stack enforces.

### 3. Function calls
```
One function pauses.
Another function runs.
When the inner one finishes, control comes back.
```

Consider this code:
```
main()
  └── funA()
        └── funB()
```

Execution flow:
```
main() starts

funA() pauses main()

funB() pauses funA()
```

Now returns happen like this:
```
funB() finishes
funA() resumes
main() resumes
```

Last function in -> first function out.

That `coming back` is Stack working silently behind the scenes.



Undo actions, brackets, and function calls
all trust the same idea:

> Handle the most recent thing first.

That idea is Stack.

