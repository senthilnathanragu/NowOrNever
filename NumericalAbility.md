# TCS NQT — Numerical Ability: Complete Preparation Guide

**Section Overview:** 25 questions | 25 minutes | Moderate to High difficulty
The key is **speed + accuracy**. You need to solve each question in roughly 60 seconds. This guide is built around that reality.

---

## 📌 TOPICS COVERED IN TCS NQT NUMERICAL ABILITY

Based on previous TCS NQT papers, the topics are:

1. Number Systems
2. LCM & HCF
3. Percentages
4. Profit & Loss
5. Simple Interest & Compound Interest
6. Ratio & Proportion
7. Time, Speed & Distance
8. Time & Work
9. Averages
10. Ages
11. Mixtures & Alligations
12. Permutation & Combination
13. Probability
14. Mensuration (2D & 3D)
15. Progressions (AP & GP)

---

## 1. NUMBER SYSTEMS

### Core Concepts

**Divisibility Rules — Memorize These:**

| Divisor | Rule |
|---|---|
| 2 | Last digit even |
| 3 | Sum of digits divisible by 3 |
| 4 | Last 2 digits divisible by 4 |
| 5 | Last digit 0 or 5 |
| 6 | Divisible by both 2 and 3 |
| 7 | Double last digit, subtract from rest, result divisible by 7 |
| 8 | Last 3 digits divisible by 8 |
| 9 | Sum of digits divisible by 9 |
| 11 | (Sum of odd-position digits) − (Sum of even-position digits) = 0 or multiple of 11 |

**Types of Numbers:**
- Natural Numbers: 1, 2, 3, ...
- Whole Numbers: 0, 1, 2, 3, ...
- Integers: ...-2, -1, 0, 1, 2...
- Prime Numbers: Divisible only by 1 and itself (2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47...)
- Co-prime Numbers: Two numbers whose HCF = 1 (e.g., 8 and 15)

**Finding Number of Factors:**
Express number as: N = a^p × b^q × c^r
Number of factors = (p+1)(q+1)(r+1)

Example: 360 = 2³ × 3² × 5¹ → Factors = (3+1)(2+1)(1+1) = 4×3×2 = **24 factors**

**Unit Digit Cycles (Critical for TCS):**

| Base | Cycle | Cycle Length |
|---|---|---|
| 2 | 2,4,8,6 | 4 |
| 3 | 3,9,7,1 | 4 |
| 4 | 4,6 | 2 |
| 7 | 7,9,3,1 | 4 |
| 8 | 8,4,2,6 | 4 |
| 9 | 9,1 | 2 |
| 0,1,5,6 | Always same | 1 |

**How to use:** To find unit digit of 7^43 → 43 ÷ 4 = remainder 3 → 3rd in cycle (7,9,3,1) → **Unit digit = 3**

**Remainder Theorems:**
- **Fermat's Little Theorem:** If p is prime and HCF(a,p)=1, then a^(p-1) ≡ 1 (mod p)
- **Remainder of (a×b)/n** = [(a mod n) × (b mod n)] / n

### Practice Problems

**Q1.** What is the unit digit of 3^171 + 6^59 + 7^45?
- 3^171: 171÷4 = rem 3 → unit digit of 3^3 = 7
- 6^59: always 6
- 7^45: 45÷4 = rem 1 → unit digit of 7^1 = 7
- Sum unit digit: 7+6+7 = 20 → **Unit digit = 0**

**Q2.** How many prime numbers exist between 1 and 50?
Answer: 2,3,5,7,11,13,17,19,23,29,31,37,41,43,47 → **15 primes**

**Q3.** Find the remainder when 2^50 is divided by 7.
- By Fermat: 2^6 ≡ 1 (mod 7)
- 50 = 6×8 + 2 → 2^50 ≡ 2^2 = 4 (mod 7) → **Remainder = 4**

---

## 2. LCM & HCF

### Core Formulas

- **HCF × LCM = Product of two numbers** (only for 2 numbers)
- HCF of fractions = HCF of numerators / LCM of denominators
- LCM of fractions = LCM of numerators / HCF of denominators

**Finding HCF by Euclid's Division:**
HCF(48, 18): 48 = 18×2 + 12 → 18 = 12×1 + 6 → 12 = 6×2 + 0 → **HCF = 6**

**Key Problem Types:**

**Type 1 — Largest number that divides a, b, c leaving same remainder r:**
Answer = HCF(a−r, b−r, c−r)

**Type 2 — Largest number dividing a, b, c leaving remainders p, q, r:**
Answer = HCF(a−p, b−q, c−r)

**Type 3 — Smallest number divisible by a, b, c:**
Answer = LCM(a, b, c)

**Type 4 — Smallest number which when divided by a, b, c leaves remainder r:**
Answer = LCM(a, b, c) + r

### Practice Problems

**Q1.** Find the largest number that divides 245, 1029, and 1365 leaving remainder 5 in each case.
- 245−5=240, 1029−5=1024, 1365−5=1360
- HCF(240, 1024, 1360)
- HCF(240,1024): 1024=240×4+64 → 240=64×3+48 → 64=48×1+16 → 48=16×3 → HCF=16
- HCF(16, 1360): 1360=16×85 → **HCF = 16**

**Q2.** The LCM of two numbers is 2310, their HCF is 30. If one number is 210, find the other.
- Other number = (LCM × HCF) / First = (2310 × 30) / 210 = **330**

**Q3.** What is the smallest number that, when divided by 12, 18, and 24, leaves a remainder of 7?
- LCM(12,18,24) = 72
- Answer = 72 + 7 = **79**

---

## 3. PERCENTAGES

### Core Formulas

- Percentage = (Value / Total) × 100
- **Percentage Change** = [(New − Old) / Old] × 100
- If A is x% more than B → B is [x/(100+x) × 100]% less than A
- If A is x% less than B → B is [x/(100−x) × 100]% more than A

**Successive Percentage Changes:**
If price increases by a% then b%, net change = a + b + (ab/100)%

Example: 20% increase then 10% decrease → 20 − 10 + (20×(−10)/100) = 10 − 2 = **8% net increase**

**Shortcut Table — Fraction ↔ Percentage (Memorize all):**

| Fraction | % |
|---|---|
| 1/2 | 50% |
| 1/3 | 33.33% |
| 1/4 | 25% |
| 1/5 | 20% |
| 1/6 | 16.67% |
| 1/7 | 14.28% |
| 1/8 | 12.5% |
| 1/9 | 11.11% |
| 1/10 | 10% |
| 1/11 | 9.09% |
| 1/12 | 8.33% |

### Practice Problems

**Q1.** A number is increased by 20% and then decreased by 20%. What is the net change?
- Net = 20 + (−20) + (20×(−20)/100) = 0 − 4 = **4% decrease**

**Q2.** In an election between 2 candidates, 70% of voters voted. Candidate A got 52% of votes cast and won by 2800 votes. Find total voters.
- Votes for A = 52%, Votes for B = 48%, Difference = 4% of total votes cast
- 4% of (70% of Total) = 2800
- Total = 2800 / (0.04 × 0.70) = 2800/0.028 = **1,00,000**

**Q3.** A shopkeeper marks price 25% above cost price and gives 10% discount. Find profit%.
- Let CP = 100, MP = 125, SP = 125 × 0.90 = 112.5
- Profit = 12.5% → **12.5%**

---

## 4. PROFIT & LOSS

### Core Formulas

- Profit = SP − CP | Loss = CP − SP
- Profit% = (Profit/CP) × 100
- SP = CP × (100 + P%) / 100
- CP = SP × 100 / (100 + P%)
- **Dishonest Shopkeeper:** Profit% = (True weight − False weight) / False weight × 100

**When SP of x articles = CP of y articles:**
- Profit% = (y−x)/x × 100 (if y>x)
- Loss% = (x−y)/x × 100 (if x>y)

**Two articles sold at same price, one at x% profit and other at x% loss:**
- Net result is always a **LOSS**
- Loss% = (x/10)² = x²/100 %

### Practice Problems

**Q1.** An article is sold at 20% profit. If CP and SP are both increased by ₹100, the profit% becomes 15%. Find CP.
- Original: SP = 1.2×CP
- New: (1.2CP + 100) / (CP + 100) = 1.15
- 1.2CP + 100 = 1.15CP + 115
- 0.05CP = 15 → **CP = ₹300**

**Q2.** A trader sells two bikes at ₹39,600 each. On one he gains 10% and on the other he loses 10%. Find net profit or loss%.
- Net Loss% = (10)²/100 = **1% loss**

**Q3.** By selling 45 oranges for ₹40, a man loses 20%. How many oranges should he sell for ₹40 to gain 20%?
- CP of 45 oranges: SP = 40 at 20% loss → CP = 40 × 100/80 = 50
- For 20% gain: SP should be 50 × 120/100 = 60 for 45 oranges
- For ₹40: 45 × 40/60 = **30 oranges**

---

## 5. SIMPLE INTEREST & COMPOUND INTEREST

### Core Formulas

**Simple Interest:**
- SI = PRT/100
- Amount = P + SI = P(1 + RT/100)

**Compound Interest:**
- A = P(1 + R/100)^T
- CI = A − P
- When compounded half-yearly: A = P(1 + R/200)^(2T)
- When compounded quarterly: A = P(1 + R/400)^(4T)

**Key Relationships:**
- SI for 2 years = 2 × (SI for 1 year)
- CI for 2 years − SI for 2 years = P(R/100)²
- CI for 3 years − SI for 3 years = P(R/100)²(R/100 + 3)

**Difference formula (very useful):**
CI − SI for 2 years = P × (R/100)²

### Practice Problems

**Q1.** A sum of money doubles itself at SI in 8 years. In how many years will it triple?
- If P doubles, SI = P, so P×R×8/100 = P → R = 12.5%
- For triple: 2P = P×12.5×T/100 → T = **16 years**

**Q2.** The CI on ₹6000 for 2 years at 5% p.a. is:
- A = 6000 × (1.05)² = 6000 × 1.1025 = ₹6615
- CI = **₹615**

**Q3.** The difference between CI and SI on ₹8000 for 2 years at 5% p.a. is:
- Difference = P × (R/100)² = 8000 × (0.05)² = 8000 × 0.0025 = **₹20**

---

## 6. RATIO & PROPORTION

### Core Concepts

- If a:b = c:d, then ad = bc (Cross multiplication)
- **Componendo:** (a+b)/(a−b) = (c+d)/(c−d)
- If a:b and b:c are given, find a:b:c by making b common
- **Fourth Proportional** to a, b, c = bc/a
- **Third Proportional** to a, b = b²/a
- **Mean Proportional** to a, b = √(ab)

**Dividing in ratio:** If total T divided in ratio a:b:c
- First part = T × a/(a+b+c)

### Practice Problems

**Q1.** Salaries of A, B, C are in ratio 2:3:5. If each gets ₹2000 increment, new ratio is 40:57:95. Find B's salary.
- 2x+2000 / 3x+2000 = 40/57
- 57(2x+2000) = 40(3x+2000)
- 114x + 114000 = 120x + 80000
- 6x = 34000 → x = 34000/6... let me try differently
- Actually: check if (2x+2000)/(5x+2000) = 40/95 = 8/19
- 19(2x+2000) = 8(5x+2000)
- 38x + 38000 = 40x + 16000
- 2x = 22000 → x = 11000
- B's salary = 3x = **₹33,000**

**Q2.** Two numbers are in ratio 3:4. If 6 is added to each, ratio becomes 4:5. Find the numbers.
- 3x+6 / 4x+6 = 4/5
- 5(3x+6) = 4(4x+6) → 15x+30 = 16x+24 → x = 6
- Numbers: **18 and 24**

---

## 7. TIME, SPEED & DISTANCE

### Core Formulas

- Speed = Distance / Time
- **Conversion:** x km/h = x × (5/18) m/s | x m/s = x × (18/5) km/h

**Relative Speed:**
- Same direction: |S1 − S2|
- Opposite direction: S1 + S2

**Trains:**
- Train crossing a pole/person: Time = Length of train / Speed
- Train crossing a platform: Time = (Length of train + Length of platform) / Speed
- Two trains crossing each other: Time = (L1 + L2) / Relative Speed

**Boats & Streams:**
- Downstream speed = B + S (B=boat speed, S=stream speed)
- Upstream speed = B − S
- B = (Downstream + Upstream) / 2
- S = (Downstream − Upstream) / 2

**Average Speed:**
- When equal DISTANCES at speeds s1 and s2: Avg speed = 2s1s2/(s1+s2)
- When equal TIMES at speeds s1 and s2: Avg speed = (s1+s2)/2

### Practice Problems

**Q1.** A train 240m long passes a pole in 24 seconds and a platform in 44 seconds. Find platform length.
- Speed = 240/24 = 10 m/s
- Distance in 44 sec = 440 m = 240 + Platform
- Platform = **200 m**

**Q2.** A man can row 8 km/h in still water. River flows at 2 km/h. Time to row 28 km downstream?
- Downstream = 8+2 = 10 km/h
- Time = 28/10 = **2.8 hours = 2 hrs 48 min**

**Q3.** Two cars start from A and B (120 km apart) toward each other at 40 and 60 km/h. When do they meet?
- Relative speed = 100 km/h
- Time = 120/100 = **1.2 hours = 72 minutes**

---

## 8. TIME & WORK

### Core Concepts

- If A completes work in n days → A's 1 day work = 1/n
- **LCM method (fastest approach):** Assume total work = LCM of all days

**Pipes & Cisterns:**
- Inlet pipe fills in n hours → work/hour = +1/n
- Outlet pipe empties in n hours → work/hour = −1/n

**Efficiency concept:**
If A is x times as efficient as B, A takes (1/x) times the time B takes.

### Practice Problems

**Q1.** A can do work in 15 days, B in 20 days. They work together for 4 days then A leaves. How many more days for B to finish?
- LCM(15,20) = 60 units. A = 4/day, B = 3/day
- Together in 4 days = 28 units done
- Remaining = 32 units, B alone = 32/3 = **10⅔ days**

**Q2.** A pipe fills tank in 6 hours, another fills in 4 hours, a drain empties in 12 hours. If all open, time to fill?
- Combined rate = 1/6 + 1/4 − 1/12 = 2/12 + 3/12 − 1/12 = 4/12 = 1/3
- Time = **3 hours**

**Q3.** 10 men can complete a job in 14 days. How many days will 4 men take?
- Man-days = 140
- 4 men: 140/4 = **35 days**

---

## 9. AVERAGES

### Core Formulas

- Average = Sum / Count
- If average of n numbers is A, and a new number x is added:
  - New average = (nA + x) / (n+1)
- If a number x is replaced by y:
  - Change in average = (y−x)/n

**Weighted Average:**
= (n1×A1 + n2×A2) / (n1 + n2)

### Practice Problems

**Q1.** Average of 20 numbers is 35. Later found one number 56 was misread as 65. Correct average?
- Correct sum = 20×35 − 65 + 56 = 700 − 9 = 691
- New average = 691/20 = **34.55**

**Q2.** Average age of class of 30 students is 14 years. Teacher's age included, average becomes 15. Find teacher's age.
- Sum increases by 31×15 − 30×14 = 465 − 420 = 45 → No: teacher's age = 15×31 − 14×30 = 465 − 420 = **45 years**

---

## 10. PERMUTATION & COMBINATION

### Core Formulas

- **nPr** = n! / (n−r)! → Arrangements (Order matters)
- **nCr** = n! / [r!(n−r)!] → Selections (Order doesn't matter)
- nCr = nC(n−r)
- nC0 = nCn = 1

**Key Arrangements:**
- n distinct items in a line: n!
- n items in a circle: (n−1)!
- n items with r identical: n!/r!
- Words from "WORD" with repeated letters: n!/(repetition factorials)

### Practice Problems

**Q1.** How many 4-digit numbers can be formed using 1−9 without repetition?
- 9P4 = 9×8×7×6 = **3024**

**Q2.** In how many ways can 5 boys and 3 girls sit in a row such that no two girls are together?
- Arrange 5 boys: 5! = 120 ways
- Gaps between boys: _ B _ B _ B _ B _ B _ (6 gaps)
- Choose 3 gaps for girls: 6P3 = 120
- Total = 120 × 120 = **14400**

**Q3.** From 6 men and 4 women, select a committee of 5 with at least 2 women.
- 2W+3M: 4C2 × 6C3 = 6×20 = 120
- 3W+2M: 4C3 × 6C2 = 4×15 = 60
- 4W+1M: 4C4 × 6C1 = 1×6 = 6
- Total = **186**

---

## 11. PROBABILITY

### Core Formulas

- P(A) = Favourable outcomes / Total outcomes
- 0 ≤ P(A) ≤ 1
- P(A') = 1 − P(A)
- P(A∪B) = P(A) + P(B) − P(A∩B)
- **Independent events:** P(A∩B) = P(A) × P(B)
- **Mutually Exclusive:** P(A∩B) = 0

**Card Problems (52 cards):**
- 4 suits: Hearts, Diamonds, Clubs, Spades (13 each)
- Each suit: A, 2, 3, 4, 5, 6, 7, 8, 9, 10, J, Q, K
- Face cards = 12 (J, Q, K of each suit)

### Practice Problems

**Q1.** Two dice are rolled. Probability that sum = 8?
- Favourable: (2,6),(3,5),(4,4),(5,3),(6,2) = 5 outcomes
- Total = 36 → P = **5/36**

**Q2.** A bag has 5 red, 4 blue, 3 green balls. Two drawn at random. P(both red)?
- 5C2/12C2 = 10/66 = **5/33**

**Q3.** P(A) = 2/5, P(B) = 3/10, A and B are independent. Find P(A∪B).
- P(A∩B) = 2/5 × 3/10 = 6/50 = 3/25
- P(A∪B) = 2/5 + 3/10 − 3/25 = 10/25 + 7.5/25 − 3/25 = **59/100**

---

## 12. MENSURATION

### 2D Shapes

| Shape | Area | Perimeter |
|---|---|---|
| Square (a) | a² | 4a |
| Rectangle (l,b) | lb | 2(l+b) |
| Triangle (b,h) | ½bh | a+b+c |
| Equilateral △ (a) | (√3/4)a² | 3a |
| Circle (r) | πr² | 2πr |
| Trapezium | ½(a+b)h | sum of sides |
| Rhombus | ½ d1×d2 | 4a |

### 3D Shapes

| Shape | Volume | Surface Area |
|---|---|---|
| Cube (a) | a³ | 6a² |
| Cuboid (l,b,h) | lbh | 2(lb+bh+hl) |
| Cylinder (r,h) | πr²h | 2πr(r+h) |
| Cone (r,h) | ⅓πr²h | πr(r+l), l=√(r²+h²) |
| Sphere (r) | 4/3 πr³ | 4πr² |

---

## 13. PROGRESSIONS (AP & GP)

### Arithmetic Progression (AP)

- General term: aₙ = a + (n−1)d
- Sum of n terms: Sₙ = n/2 × [2a + (n−1)d] = n/2 × (first + last)
- If three numbers in AP: use a−d, a, a+d

### Geometric Progression (GP)

- General term: aₙ = ar^(n−1)
- Sum of n terms: Sₙ = a(rⁿ − 1)/(r−1) when r≠1
- Sum to infinity: S∞ = a/(1−r) when |r|<1

### Practice Problems

**Q1.** Find the 20th term of AP: 3, 7, 11, 15...
- a=3, d=4, a20 = 3 + 19×4 = **79**

**Q2.** Sum of AP: 2+5+8+...+59
- n = (59−2)/3 + 1 = 20 terms
- Sum = 20/2 × (2+59) = **610**

**Q3.** Find sum of GP: 3+6+12+...upto 8 terms
- a=3, r=2, S8 = 3(2⁸−1)/(2−1) = 3×255 = **765**

---

## ⚡ SPEED MATH SHORTCUTS (Must Know for TCS)

### Squaring Numbers

- **Numbers ending in 5:** 75² → 7×8 = 56, append 25 → **5625**
- **Near 100:** 97² → (97−3)=94, (3²)=09 → **9409**
- **Near 50:** 47² → (47−50)=−3, (50−3)²=47²... Use (50−3)² = 2500−300+9 = **2209**

### Multiplication Shortcuts

- Multiply by 99: n×99 = n×100 − n
- Multiply by 11: 36×11 → 3_(3+6)_6 → **396**

### Percentage to Fraction Conversion

- 12.5% = 1/8 | 37.5% = 3/8 | 62.5% = 5/8 | 87.5% = 7/8
- 16.67% = 1/6 | 33.33% = 1/3 | 66.67% = 2/3 | 83.33% = 5/6

---

## 📅 TOPIC-WISE WEIGHTAGE IN TCS NQT

| Topic | Expected Questions |
|---|---|
| Percentages, Profit & Loss | 3−4 |
| Time-Speed-Distance, Time-Work | 3−4 |
| Number System | 2−3 |
| SI & CI | 2 |
| P&C and Probability | 2−3 |
| Ratio & Averages | 2 |
| Mensuration | 1−2 |
| LCM & HCF | 1 |
| Progressions | 1 |

---

## 🎯 EXAM-DAY STRATEGY

**Attempt Order:**
1. First pass through all 25 — solve what you can in under 45 seconds
2. Second pass — tackle medium difficulty (45−90 sec)
3. Third pass — hard problems with remaining time

**Elimination Technique:** TCS options are designed so you can often eliminate 2 wrong answers quickly, turning a 25% guess into a 50% educated guess.

**Don't get stuck.** If a problem takes more than 90 seconds, mark and move on. Attempting 22 questions with 95% accuracy beats attempting 25 with 70% accuracy.

---

Whenever you're ready, tell me the next topic — **Verbal Ability** or **Reasoning Ability** — and I'll bring the same level of detail. You've already taken the first step. Keep going. 💪
