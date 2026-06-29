# Sliding Window

> **Version:** 0.1
> **Last Updated:** June 2026

---

# Purpose

The Sliding Window technique is used to efficiently solve problems involving **contiguous** subarrays or substrings while avoiding repeated computation.

Instead of recalculating information for every possible window, we maintain a window and update it incrementally.

---

# Mental Model

Think of the window as a **candidate solution**.

The algorithm repeatedly performs four operations:

```
Expand Window
       ↓
Window becomes invalid?
       ↓
Restore Invariant
       ↓
Window becomes valid
       ↓
Update Answer
```

Everything in a sliding window problem revolves around maintaining a valid window.

---

# Problem Recognition

Consider Sliding Window when the problem contains words like:

* Contiguous
* Continuous
* Subarray
* Substring
* Longest
* Shortest
* Maximum
* Minimum
* Fixed length
* At most
* Exactly

---

# Sliding Window Types

## 1. Fixed Window

Characteristics

* Window size never changes.
* Left pointer moves whenever right pointer expands beyond the required size.

Examples

* Maximum Average Subarray
* Maximum Number of Vowels

Framework

```
Expand

If window size > k

    Remove left

Update answer
```

---

## 2. Variable Window

Characteristics

* Window grows until it violates a constraint.
* Shrinks until the invariant is restored.

Examples

* Longest substring without repeating characters
* Maximum Consecutive Ones III
* Longest Subarray After Deleting One Element

Framework

```
Expand

Restore invariant

Update answer
```

---

# First-Principles Framework

Before writing any code, answer these questions.

## Question 1

What does the window represent?

Examples

* Current candidate substring
* Current candidate subarray

Never start coding until this is clear.

---

## Question 2

What makes the window valid?

This becomes the invariant.

Examples

```
zeroCount <= k

duplicateCount == 0

windowSize == k

sum <= target
```

---

## Question 3

How is the invariant restored?

Normally

```
while(window is invalid){

    shrink

}
```

---

## Question 4

When can the window contribute to the answer?

Examples

Only after

* invariant restored
* fixed size reached

---

## Question 5

What exactly should be calculated?

Examples

Window size

```
right-left+1
```

or

Window size after deleting one element

```
right-left
```

The formula should always be derived from what the window represents.

---

# Invariant

Definition

An invariant is a condition that is always true before the answer is updated.

Examples

Maximum Consecutive Ones III

```
zeroCount <= k
```

Longest Subarray After Deleting One Element

```
zeroCount <= 1
```

Do not update the answer until the invariant holds.

---

# State vs Event Thinking ⭐

One of the most important interview lessons.

## Incorrect Thinking

"I just saw a zero."

"zeroCount became k."

"I found a duplicate."

These describe events.

---

## Correct Thinking

"The window is valid."

"The invariant holds."

"This window is now a candidate."

These describe state.

Senior engineers reason about state rather than individual events.

---

# Communication

Avoid implementation-first explanations.

Poor

> Arrays are zero-indexed.

Better

> The window represents the original subarray. Since one element must be deleted, the resulting size becomes windowSize - 1.

Always explain why before explaining how.

---

# Responsibilities

Never mix responsibilities.

```
Expand Window

↓

Restore Invariant

↓

Update Answer
```

Each step should have exactly one responsibility.

---

# Common Mistakes

* Updating the answer before restoring the invariant.
* Confusing event-based reasoning with state-based reasoning.
* Explaining formulas using implementation details rather than algorithmic reasoning.
* Mixing shrinking logic with answer computation.
* Forgetting to define what the window represents.

---

# Personal Coaching Notes

## Observation #1

Current tendency

Reason using events.

Desired behavior

Reason using state and invariants.

Status

Improving

---

## Observation #2

Current tendency

Explain implementation.

Desired behavior

Explain reasoning.

Status

Improving

---

## Observation #3

Strength

Quickly identifies the sliding window pattern.

Next level

Derive the algorithm from first principles instead of pattern recognition.

---

# Interview Checklist

Before writing code

* [ ] What does the window represent?
* [ ] What invariant makes it valid?
* [ ] When is the window allowed to update the answer?
* [ ] Why is my answer formula correct?
* [ ] Can I explain the algorithm without mentioning code?

---

# Revision Checklist (30 Seconds)

1. Window representation
2. Invariant
3. Expand
4. Restore
5. Update
6. Explain why
7. Complexity

---

# Problems Covered

| Problem                                     | Lesson Learned                              |
| ------------------------------------------- | ------------------------------------------- |
| Maximum Average Subarray                    | Fixed window                                |
| Maximum Number of Vowels                    | Fixed window with running count             |
| Maximum Consecutive Ones III                | Variable window and invariants              |
| Longest Subarray After Deleting One Element | Window interpretation and answer derivation |

---

# Complexity

Most sliding window problems

Time

O(n)

Space

O(1)

unless additional data structures are required.

---

# Version History

## v0.1

Initial framework created.

Topics included

* Fixed vs Variable window
* Invariant thinking
* State vs Event reasoning
* Staff interview communication
* Personal coaching notes
* Revision checklist
