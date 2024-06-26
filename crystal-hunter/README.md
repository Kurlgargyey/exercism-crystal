# Crystal Hunter

Welcome to Crystal Hunter on Exercism's Crystal Track.
If you need help running the tests or submitting your code, check out `HELP.md`.
If you get stuck on the exercise, check out `HINTS.md`, but try and solve it without using those first :)

## Introduction

Crystal has a type known as [`Bool`][bools].
It represents the values `true` and `false`.

## Logical operators

Crystal has three logical operators (`!`, `||`, `&&`), which combine Bools and make expressions that produce different values.

### And(`&&`)

The [_and_ operator][and] in Crystal is represented by `&&` and returns `true` if both values are `true`; otherwise, it returns `false`.
When using the _and_ operator, one Bool is placed on the right side of the `&&` and another on the left side.

```crystal
true && true
# => true

true && false
# => false
```

### Or(`||`)

The [_or_ operator][or] in Crystal is represented by `||` and returns `true` if **at least one** of the values given is `true`. 
If both of the values are `false`, then it returns `false`.
When using the _or_ operator, one Bool should be placed on the right side of the `||` and another on the left.

```crystal
true || true
# => true

true || false
# => true

false || false
# => false
```

### Not(`!`)

The _not_ operator in Crystal is represented by `!` and returns `true` if the given Bool is `false` and returns `false` if `true` is provided.
When using the _not_ operator, one Bool should be placed after the operator (`!`).

```crystal
!true
# => false

!false
# => true
```

## Using parentheses(`()`)

When working with booleans, you can use parentheses to decide which Bools to evaluate first.
The result can differ depending on how the parentheses are used.
In Crystal, what is in parentheses is evaluated first.

```crystal
true && false && false || true
# => true

true && false && (false || true)
# => false
```

Since what is in parentheses is evaluated first, the _not_ operator will apply to the expression inside parentheses in the following example.

```crystal
!true && false
# => false

!(true && false)
# => true
```

~~~~exercism/note
You should only use parentheses when they affect the result; otherwise, they should be omitted.
~~~~

[bools]: https://crystal-lang.org/reference/latest/syntax_and_semantics/literals/bool.html
[and]: https://crystal-lang.org/reference/latest/syntax_and_semantics/and.html
[or]: https://crystal-lang.org/reference/latest/syntax_and_semantics/or.html

## Instructions

You are in the process of developing the new highly appreciated game **Crystal Hunter**.
In the game, you are a character who moves around and collects crystals.
The player wins by picking up all the crystals.
If the player comes in contact with a bandit, they will lose all their crystals and the game.
There is an exception to this rule: the player can have an active power-up that makes them invisible to the bandits.

Your goal is to write some rules that will be used in the game.

## 1. Define if character gets bonus points

In the game, the character will get bonus points if they touch a bandit while having a power-up.

Define the `Rules#bonus_points?` method that takes two arguments (_if the character has an active power-up_ and _if the character is touching a bandit_) and returns a boolean value that tells whether the character will get bonus points.
The method should return `true` only if the character has a power-up active and is touching a bandit and `false` otherwise.

```Crystal
Rules.new.bonus_points?(false, true)
# => false
```

## 2. Define if character scores

The player gets points in the game when picking up a crystal or a power-up.

Define the `Rules#score?` method, which takes two arguments (_if the character is touching a power-up_ and _if the character is touching a crystal_) and returns a boolean value indicating whether the character scored or not.
The method should return `true` if the character touches a power-up or a crystal and return `false` otherwise.

```crystal
Rules.new.score?(true, true)
# => true
```

## 3. Define if character loses

Define the `Rules#lose?` method, which takes two arguments (_if the character has a power-up active_ and _if the character is touching a bandit_) and returns a boolean value that indicates whether the character loses or not.
The method should return `true` if the character touches a bandit and does not have a power-up active and return `false` otherwise.

```crystal
Rules.new.lose?(false, true)
# => true
```

## 4. Define if character wins

Define the `Rules#win?` method, which takes three arguments (_if the character has picked up all of the crystals_, _if the character has a power-up active_, and _if the character is touching a bandit_) and returns a boolean value indicating whether the character wins or not.
The method should return `true` if the character has gathered all crystals and has not lost based on the arguments defined in part 3 and return `false` otherwise.

```crystal
Rules.new.win?(false, true, false)
# => false
```

## Source

### Created by

- @meatball133

### Contributed to by

- @andrerfcsantos
- @angelikatyborska
- @glennj
- @ryanplusplus