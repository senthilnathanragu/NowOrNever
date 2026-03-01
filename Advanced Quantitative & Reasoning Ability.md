# TCS NQT — Advanced Quantitative & Reasoning Ability: Complete Prime Package Guide

**Section Overview:** 25 questions | 25 minutes | Highest difficulty in the entire exam
This section is what **separates Prime from Smart and Ninja packages.** The questions here require you to think faster, apply formulas deeper, and combine multiple concepts in a single problem. This guide is built to take you to that level.

---

## 📌 TOPICS COVERED IN ADVANCED QR

1. Advanced Number Theory
2. Advanced Algebra & Equations
3. Advanced Geometry & Coordinate Geometry
4. Advanced Permutation & Combination
5. Advanced Probability
6. Data Interpretation (DI)
7. Advanced Logical Reasoning
8. Functions, Progressions & Series
9. Set Theory (Advanced)
10. Inequalities & Modular Arithmetic
11. Matrices & Determinants (Basic)
12. Advanced Puzzles & Critical Reasoning
13. Clocks, Calendars & Advanced Arrangements
14. Miscellaneous High-Order Problems

---

## 1. ADVANCED NUMBER THEORY

### 1.1 Divisibility — Deep Concepts

**Wilson's Theorem:**
For any prime p: (p−1)! ≡ −1 (mod p)
Example: (6)! mod 7 = 720 mod 7 = 6 ≡ −1 (mod 7) ✅

**Application:** Remainder of (p−1)!/p = p−1 (for prime p)

**Fermat's Little Theorem (Advanced):**
If p is prime and gcd(a,p) = 1, then:
a^(p−1) ≡ 1 (mod p)

**Euler's Theorem (Generalization):**
a^φ(n) ≡ 1 (mod n), where φ(n) = Euler's Totient Function

**Euler's Totient φ(n):**
For n = p₁^a × p₂^b × p₃^c...
φ(n) = n × (1 − 1/p₁) × (1 − 1/p₂) × (1 − 1/p₃)...

Examples:
- φ(10) = 10 × (1−1/2) × (1−1/5) = 10 × 1/2 × 4/5 = **4**
- φ(12) = 12 × (1−1/2) × (1−1/3) = 12 × 1/2 × 2/3 = **4**
- φ(36) = 36 × (1−1/2) × (1−1/3) = 36 × 1/2 × 2/3 = **12**

**Application in Remainders:**
Find remainder of 3^100 divided by 7.
φ(7) = 6 → 3^6 ≡ 1 (mod 7)
100 = 6×16 + 4 → 3^100 = (3^6)^16 × 3^4 ≡ 1 × 81 ≡ 81 mod 7
81 = 7×11 + 4 → **Remainder = 4**

---

### 1.2 Highest Power of a Prime in n!

**Legendre's Formula:**
Highest power of prime p in n! = ⌊n/p⌋ + ⌊n/p²⌋ + ⌊n/p³⌋ + ... (until floor = 0)

**Example:** Highest power of 2 in 20!
= ⌊20/2⌋ + ⌊20/4⌋ + ⌊20/8⌋ + ⌊20/16⌋
= 10 + 5 + 2 + 1 = **18**

**Example:** Highest power of 5 in 100!
= ⌊100/5⌋ + ⌊100/25⌋ + ⌊100/125⌋
= 20 + 4 + 0 = **24**

**Finding Trailing Zeros in n!:**
Trailing zeros = min(power of 2, power of 5) = always power of 5
Trailing zeros in 100! = **24**

---

### 1.3 Chinese Remainder Theorem (CRT)

Find a number that satisfies multiple remainder conditions simultaneously.

**Example:**
Find the smallest number that gives:
- Remainder 2 when divided by 3
- Remainder 3 when divided by 5
- Remainder 2 when divided by 7

**Method:**
x ≡ 2 (mod 3) → x = 3k + 2
x ≡ 3 (mod 5) → x = 5m + 3
x ≡ 2 (mod 7) → x = 7n + 2

From first: x = 2, 5, 8, 11, 14, 17, 20, 23...
From second: x = 3, 8, 13, 18, 23, 28...
Common so far: x = 8, 23, 38... (differences of LCM(3,5)=15)
From third: x must also ≡ 2 (mod 7): 8 mod 7 = 1 ✗, 23 mod 7 = 2 ✅
**Answer: 23**

---

### 1.4 Last Two Digits (Advanced)

**Finding last two digits = finding remainder when divided by 100**

**Rules for Last Two Digits:**
- Last two digits of 2^1=02, 2^2=04, 2^3=08... pattern repeats every 20 powers for numbers ending in 2,4,6,8
- For odd numbers: use Euler's theorem with φ(100) = 40
- So for any odd number coprime to 100: a^40 ≡ 1 (mod 100)

**Example:** Last two digits of 3^124
φ(100) = 40. 124 = 40×3 + 4
Last two digits of 3^4 = 81 → **Last two digits: 81**

**Example:** Last two digits of 7^2023
2023 = 40×50 + 23. Find 7^23.
7^1=07, 7^2=49, 7^4=01 (mod 100? No: 49²=2401, last two=01)
7^4 ≡ 01 (mod 100). 23 = 4×5 + 3. 7^20 ≡ 01. 7^23 = 7^20 × 7^3 = 01 × 343 → last two = **43**

---

### 1.5 Practice Problems — Number Theory

**Q1.** Find the remainder when 2^256 is divided by 17.
φ(17)=16. 256=16×16. 2^256=(2^16)^16 ≡ 1^16 = 1 (mod 17). **Remainder = 1**

**Q2.** How many trailing zeros in 125!?
= ⌊125/5⌋ + ⌊125/25⌋ + ⌊125/125⌋ = 25+5+1 = **31**

**Q3.** Find remainder of 7^201 divided by 100.
φ(100)=40. 201=40×5+1. 7^201 ≡ 7^1 = **7**

**Q4.** Find the number of zeros at the end of 20! × 30!
Zeros in 20! = ⌊20/5⌋+⌊20/25⌋ = 4+0 = 4
Zeros in 30! = ⌊30/5⌋+⌊30/25⌋ = 6+1 = 7
Total = **11 zeros**

**Q5.** What is the highest power of 3 in 90!?
= ⌊90/3⌋+⌊90/9⌋+⌊90/27⌋+⌊90/81⌋
= 30+10+3+1 = **44**

---

## 2. ADVANCED ALGEBRA

### 2.1 Quadratic Equations — Deep Analysis

**Quadratic:** ax² + bx + c = 0
**Roots:** α, β where:
- Sum of roots: α + β = **−b/a**
- Product of roots: α × β = **c/a**
- Discriminant: D = b² − 4ac

**Nature of Roots:**
- D > 0: Two distinct real roots
- D = 0: Two equal real roots
- D < 0: Two complex (imaginary) roots
- D is a perfect square and rational coefficients: roots are rational

**Advanced Identities using roots:**
- α² + β² = (α+β)² − 2αβ
- α³ + β³ = (α+β)³ − 3αβ(α+β)
- α² − β² = (α+β)(α−β)
- (α−β)² = (α+β)² − 4αβ

**Forming equation from roots:**
x² − (sum)x + (product) = 0

**Example:** Roots are 3+√2 and 3−√2
Sum = 6, Product = 9−2 = 7
Equation: **x² − 6x + 7 = 0**

### 2.2 Polynomial Remainder Theorem

**Remainder Theorem:** When polynomial P(x) is divided by (x−a), remainder = P(a)

**Factor Theorem:** (x−a) is a factor of P(x) if and only if P(a) = 0

**Example:** Find remainder when x³ − 6x² + 11x − 6 is divided by (x−2)
P(2) = 8 − 24 + 22 − 6 = **0** → (x−2) is actually a factor

**Example:** P(x) = x⁴ − 3x² + 2x − 5 divided by (x+1)
P(−1) = 1 − 3 − 2 − 5 = **−9** → Remainder = −9

### 2.3 Advanced Logarithms

**Core Rules:**
- log(ab) = log a + log b
- log(a/b) = log a − log b
- log(aⁿ) = n log a
- log_b(a) = 1/log_a(b) (Change of base reciprocal)
- log_b(a) = log(a)/log(b) (Change of base standard)
- log_a(a) = 1
- log_a(1) = 0

**Advanced identity:**
log_a(b) × log_b(c) × log_c(a) = 1

**Example:** If log₂3 = a and log₃5 = b, find log₂15
log₂15 = log₂(3×5) = log₂3 + log₂5
log₂5 = log₂3 × log₃5 = a × b = ab
log₂15 = a + ab = **a(1+b)**

**Example:** Solve: log(x+3) + log(x−3) = log 16 − log 1
log[(x+3)(x−3)] = log 16
x² − 9 = 16
x² = 25 → x = ±5
Since log requires positive argument: x+3>0 AND x−3>0 → x>3
**Answer: x = 5**

### 2.4 Functions & Their Properties

**Types of Functions:**
- **One-to-one (Injective):** Each element of range is mapped to by exactly one domain element
- **Onto (Surjective):** Every element of codomain is mapped to by at least one domain element
- **Bijective:** Both one-to-one and onto

**Important Functions:**
- |x| (Modulus): |x| = x if x≥0, |x| = −x if x<0
- [x] (Floor/Greatest Integer): Largest integer ≤ x → [3.7]=3, [−3.2]=−4
- {x} (Fractional Part): {x} = x − [x] → {3.7}=0.7, {−3.2}=0.8

**Composite Functions:**
(f∘g)(x) = f(g(x)) — apply g first, then f

**Inverse Functions:**
f⁻¹ exists only for bijective functions
If f(a) = b, then f⁻¹(b) = a

**Example:** f(x) = 2x+3, g(x) = x²
(f∘g)(x) = f(x²) = 2x²+3
(g∘f)(x) = g(2x+3) = (2x+3)²

**Example:** Find f⁻¹ for f(x) = (3x−1)/(x+2)
Let y = (3x−1)/(x+2) → y(x+2) = 3x−1 → xy+2y = 3x−1 → x(y−3) = −1−2y
x = (−1−2y)/(y−3) = (1+2y)/(3−y)
f⁻¹(x) = **(1+2x)/(3−x)**

### 2.5 Practice Problems — Algebra

**Q1.** If α and β are roots of x²−5x+6=0, find α³+β³.
Sum=5, Product=6. α³+β³ = (α+β)³−3αβ(α+β) = 125−3×6×5 = 125−90 = **35**

**Q2.** Find the value of log₂7 × log₇5 × log₅8.
= log₂7 × log₇5 × log₅8 = log₂8 = log₂2³ = **3**

**Q3.** For f(x) = x²+1 and g(x) = √(x−1), find (f∘g)(5).
g(5) = √4 = 2. f(2) = 4+1 = **5**

---

## 3. ADVANCED GEOMETRY & COORDINATE GEOMETRY

### 3.1 Coordinate Geometry Essentials

**Distance between two points:**
d = √[(x₂−x₁)² + (y₂−y₁)²]

**Section Formula:**
Point dividing (x₁,y₁) and (x₂,y₂) in ratio m:n internally:
P = [(mx₂+nx₁)/(m+n), (my₂+ny₁)/(m+n)]

**Midpoint Formula:**
M = [(x₁+x₂)/2, (y₁+y₂)/2]

**Area of Triangle with vertices (x₁,y₁), (x₂,y₂), (x₃,y₃):**
Area = ½|x₁(y₂−y₃) + x₂(y₃−y₁) + x₃(y₁−y₂)|

**Slope of a line:**
m = (y₂−y₁)/(x₂−x₁)
- Parallel lines: m₁ = m₂
- Perpendicular lines: m₁ × m₂ = −1
- Angle between two lines: tan θ = |m₁−m₂|/(1+m₁m₂)

**Equation of a Line:**
- Slope-intercept: y = mx + c
- Point-slope: y−y₁ = m(x−x₁)
- Two-point form: (y−y₁)/(y₂−y₁) = (x−x₁)/(x₂−x₁)
- Intercept form: x/a + y/b = 1

**Distance from point (x₀,y₀) to line ax+by+c=0:**
d = |ax₀+by₀+c|/√(a²+b²)

### 3.2 Circles

**Standard equation:** (x−h)² + (y−k)² = r²
Center = (h,k), Radius = r

**General form:** x²+y²+2gx+2fy+c=0
Center = (−g,−f), Radius = √(g²+f²−c)

**Tangent to circle at point (x₁,y₁):**
x·x₁ + y·y₁ + g(x+x₁) + f(y+y₁) + c = 0

**Condition for tangency (line y=mx+c to circle x²+y²=r²):**
c² = r²(1+m²) OR distance from center to line = radius

### 3.3 Advanced Mensuration

**Triangle Properties:**
- Heron's formula: Area = √[s(s−a)(s−b)(s−c)] where s = (a+b+c)/2
- In-radius: r = Area/s
- Circum-radius: R = abc/4×Area
- For right triangle: R = hypotenuse/2

**Regular Polygon of n sides:**
- Sum of interior angles = (n−2) × 180°
- Each interior angle = (n−2) × 180°/n
- Each exterior angle = 360°/n
- Area = (n/4) × a² × cot(π/n) where a = side length
- For regular hexagon: Area = (3√3/2)a²

**Sector & Segment (Circle):**
- Area of sector = (θ/360) × πr²
- Arc length = (θ/360) × 2πr
- Area of segment = Area of sector − Area of triangle

**Frustum (Truncated Cone):**
- Volume = (πh/3)(R²+Rr+r²) where R=larger radius, r=smaller radius
- Curved Surface Area = π(R+r)l where l = √[h²+(R−r)²] = slant height

**Prism:**
- Volume = Base Area × Height
- Lateral Surface Area = Perimeter of Base × Height

**Pyramid:**
- Volume = (1/3) × Base Area × Height
- Lateral Surface Area = (1/2) × Perimeter × Slant Height

### 3.4 Practice Problems — Geometry

**Q1.** Find the area of triangle with vertices (1,2), (4,6), (−3,−1).
Area = ½|1(6−(−1)) + 4((−1)−2) + (−3)(2−6)|
= ½|1(7) + 4(−3) + (−3)(−4)|
= ½|7 − 12 + 12|
= ½|7| = **3.5 sq units**

**Q2.** Find distance from point (2,−3) to line 3x+4y−5=0.
d = |3(2)+4(−3)−5|/√(9+16) = |6−12−5|/5 = |−11|/5 = **11/5 = 2.2 units**

**Q3.** A cone of radius 6cm and height 8cm is cut parallel to base at half its height. Find volume of frustum.
At half height (h'=4), radius of cut = 6×(4/8) = 3cm (similar triangles, r proportional to h)
Wait: At height 4 from apex, radius = 6×(4/8)=3. So frustum: R=6, r=3, h=4
V = (π×4/3)(36+18+9) = (4π/3)(63) = **84π cm³**

**Q4.** Two circles x²+y²=25 and x²+y²−6x+8y−11=0. Find distance between centers.
Circle 1: center (0,0), r₁=5
Circle 2: x²+y²−6x+8y−11=0 → (x−3)²+(y+4)²=11+9+16=36
Center (3,−4), r₂=6
Distance = √(9+16) = √25 = **5**

---

## 4. ADVANCED PERMUTATION & COMBINATION

### 4.1 Key Advanced Concepts

**Derangements (No element in original position):**
D(n) = n! × [1 − 1/1! + 1/2! − 1/3! + ... + (−1)ⁿ/n!]

D(1) = 0, D(2) = 1, D(3) = 2, D(4) = 9, D(5) = 44

**Example:** 5 letters in 5 envelopes — all mismatched:
D(5) = 5![1 − 1 + 1/2 − 1/6 + 1/24 − 1/120]
= 120[0 + 0.5 − 0.1667 + 0.0417 − 0.00833]
= 120 × 0.3667 = **44**

**Distribution Problems:**

**Identical objects into distinct boxes:**
- With no restriction: n+r−1 C r−1 (stars and bars)
- Where n = objects, r = boxes

**Distinct objects into distinct boxes:**
- With no restriction: r^n
- Each box gets at least one: Stirling numbers or inclusion-exclusion

**Example:** Distribute 5 identical balls into 3 distinct boxes (no restriction):
= 5+3−1 C 3−1 = 7C2 = **21**

**Example:** Distribute 5 identical balls into 3 boxes where each box has at least 1:
= (5−1) C (3−1) = 4C2 = **6** (stars and bars with restriction)

**Circular Arrangements (Advanced):**
- n distinct objects in a circle: (n−1)!
- n distinct objects in a circle where clockwise = anti-clockwise: (n−1)!/2
- n beads in a necklace: (n−1)!/2

**Multinomial Coefficient:**
Arrangements of n objects where p are alike, q are alike, r are alike:
= n!/(p! × q! × r!)

**Example:** Arrangements of MATHEMATICS:
M appears 2 times, A appears 2 times, T appears 2 times, rest once.
Total = 11!/(2!×2!×2!) = **4,989,600**

### 4.2 Inclusion-Exclusion Principle

|A∪B∪C| = |A|+|B|+|C| − |A∩B| − |B∩C| − |A∩C| + |A∩B∩C|

**Advanced Application:**
Numbers from 1 to 100 divisible by 2 or 3 or 5:

|A| (div by 2) = 50
|B| (div by 3) = 33
|C| (div by 5) = 20
|A∩B| (div by 6) = 16
|A∩C| (div by 10) = 10
|B∩C| (div by 15) = 6
|A∩B∩C| (div by 30) = 3

|A∪B∪C| = 50+33+20−16−10−6+3 = **74**

### 4.3 Practice Problems — P&C

**Q1.** In how many ways can 7 people be seated around a circular table if 2 specific people must always sit together?
Treat the 2 as one unit → 6 units in a circle: (6−1)! = 120. The 2 can arrange among themselves in 2! = 2 ways.
Total = 120 × 2 = **240**

**Q2.** How many 4-digit numbers have no repeated digits and are divisible by 5?
For divisibility by 5: last digit = 0 or 5.
Case 1 (last digit=0): First 3 digits from 1−9: 9×8×7 = 504
Case 2 (last digit=5): First digit from 1−9 (not 5): 8 choices. Next two from remaining 8 digits: 8×7=56. Total = 8×56 = 448
Total = 504+448 = **952**

**Q3.** 12 people are split into three groups of 4. In how many ways?
= 12C4 × 8C4 × 4C4 / 3! (divide by 3! if groups are identical)
= 495 × 70 × 1 / 6 = **5775**

**Q4.** Find number of ways to distribute 8 distinct books among 3 students such that each gets at least 1.
= 3^8 − 3×2^8 + 3×1^8 (Inclusion-Exclusion)
= 6561 − 3×256 + 3×1
= 6561 − 768 + 3 = **5796**

---

## 5. ADVANCED PROBABILITY

### 5.1 Conditional Probability

**P(A|B) = P(A∩B)/P(B)**

**Multiplication Rule:**
P(A∩B) = P(A) × P(B|A) = P(B) × P(A|B)

**Independent Events:**
P(A|B) = P(A) → P(A∩B) = P(A)×P(B)

### 5.2 Bayes' Theorem

**P(Aᵢ|B) = P(B|Aᵢ)×P(Aᵢ) / Σ[P(B|Aⱼ)×P(Aⱼ)]**

**Classic Problem:**
A factory has 3 machines M1, M2, M3 producing 50%, 30%, 20% of output respectively. Defective rates are 2%, 3%, 4%.
An item is defective. What is the probability it came from M1?

P(M1) = 0.5, P(M2) = 0.3, P(M3) = 0.2
P(D|M1) = 0.02, P(D|M2) = 0.03, P(D|M3) = 0.04

P(D) = 0.5×0.02 + 0.3×0.03 + 0.2×0.04
= 0.010 + 0.009 + 0.008 = 0.027

P(M1|D) = (0.5×0.02)/0.027 = 0.01/0.027 = **10/27**

### 5.3 Geometric Probability

**Probability based on lengths, areas, or volumes rather than discrete outcomes.**

**Example:** A point is chosen at random inside a circle of radius 4. Find probability it lies within a circle of radius 2 (concentric).
P = π×2² / π×4² = 4/16 = **1/4**

**Example:** A stick of length 1 is broken at a random point. Probability the two pieces can form a triangle? (Each piece must be less than sum of other two, but since we only have 2 pieces, no triangle possible — but if broken twice:)
For 2 pieces to form a triangle (impossible since 2 pieces can't be a triangle with 2 line segments; need 3 pieces).

Standard problem: Stick broken twice. What is probability 3 pieces form a triangle?
Answer: **1/4** (using geometric probability with 2D sample space)

### 5.4 Expected Value

E(X) = Σ [xᵢ × P(xᵢ)]

**Example:** In a game, roll a die. Get ₹10 for even number, lose ₹5 for odd number. Expected gain per game?
E = (1/2)(10) + (1/2)(−5) = 5 − 2.5 = **₹2.5 per game** (favorable)

### 5.5 Binomial Distribution (Basic)

**P(X=r) = nCr × p^r × q^(n−r)**
where n = trials, p = success probability, q = 1−p

Mean = np, Variance = npq, SD = √(npq)

**Example:** A coin tossed 8 times. Probability of exactly 5 heads?
P = 8C5 × (1/2)^5 × (1/2)^3 = 56 × (1/256) = 56/256 = **7/32**

### 5.6 Practice Problems — Probability

**Q1.** Two cards drawn without replacement from a deck. P(both aces)?
P = 4/52 × 3/51 = 12/2652 = **1/221**

**Q2.** P(A)=0.6, P(B)=0.5, P(A∩B)=0.3. Find P(A|B').
P(B') = 0.5. P(A∩B') = P(A) − P(A∩B) = 0.6−0.3 = 0.3
P(A|B') = 0.3/0.5 = **0.6**

**Q3.** In an exam, 40% students pass Math, 50% pass English, 25% pass both. A student is selected randomly. Given that she passed English, probability she also passed Math?
P(M|E) = P(M∩E)/P(E) = 0.25/0.50 = **0.5**

**Q4.** A bag has 4 white and 6 black balls. Balls drawn one by one without replacement until white ball appears. Expected number of draws?
This follows a negative hypergeometric or simpler: E(draws) = (total+1)/(white+1) = 11/5 = **2.2** (or more precisely, solve directly)
Actually: E = (n+1)/(k+1) where n=total=10, k=white=4 → E = 11/5 = **2.2**

---

## 6. DATA INTERPRETATION (DI)

### 6.1 Why DI Is Critical for Prime

DI questions appear in clusters of 4−5 questions based on one dataset. If you understand the data, all 4−5 questions are answered quickly. If you don't, you lose all 4−5. **This section can give you 4−5 quick marks or cost you 4−5 marks.**

### 6.2 Types of DI

**Type 1 — Table DI**
Data in rows and columns. Most straightforward. Questions ask for totals, averages, percentage change, ratios.

**Type 2 — Bar Graph DI**
Vertical or horizontal bars. Good for comparison across categories.

**Type 3 — Line Graph DI**
Shows trends over time. Good for growth rate, maximum increase, slope comparisons.

**Type 4 — Pie Chart DI**
Shows proportion/percentage of a whole. Questions often ask for value of a particular sector given total.

**Type 5 — Combination DI**
Two different chart types together (e.g., table + pie chart). Most complex and highest value.

### 6.3 Core DI Calculations

**Percentage Change:**
= [(New−Old)/Old] × 100

**Percentage share:**
= (Part/Total) × 100

**Ratio Comparison Shortcut:**
Instead of actual division, cross-multiply to compare ratios:
Is 17/23 > 13/18? → 17×18=306 vs 13×23=299 → 306>299 → **17/23 > 13/18**

**CAGR (Compound Annual Growth Rate):**
CAGR = (Final Value/Initial Value)^(1/n) − 1
where n = number of years

**Approximate calculations for DI speed:**

| What You Need | How to Approximate |
|---|---|
| 33% of X | X/3 |
| 25% of X | X/4 |
| 12.5% of X | X/8 |
| 37.5% of X | 3X/8 |
| 16.67% of X | X/6 |

### 6.4 Table DI — Full Worked Example

**Table: Company Sales Data (₹ Crores)**

| Year | Product A | Product B | Product C | Total |
|---|---|---|---|---|
| 2019 | 120 | 80 | 100 | 300 |
| 2020 | 150 | 90 | 60 | 300 |
| 2021 | 180 | 120 | 100 | 400 |
| 2022 | 200 | 150 | 150 | 500 |
| 2023 | 240 | 180 | 180 | 600 |

**Q1.** What is the percentage growth in total sales from 2019 to 2023?
= [(600−300)/300] × 100 = **100%**

**Q2.** In which year did Product B show the highest percentage growth over previous year?
2019→2020: [(90−80)/80]×100 = 12.5%
2020→2021: [(120−90)/90]×100 = 33.3%
2021→2022: [(150−120)/120]×100 = 25%
2022→2023: [(180−150)/150]×100 = 20%
**Answer: 2021 (33.3% growth)**

**Q3.** Product A's contribution to total sales was highest in which year?
2019: 120/300 = 40%
2020: 150/300 = 50%
2021: 180/400 = 45%
2022: 200/500 = 40%
2023: 240/600 = 40%
**Answer: 2020 (50%)**

**Q4.** If the company's profit margin on Product C is 15%, what was the profit from C in 2022?
Profit = 150 × 15/100 = **₹22.5 Crores**

**Q5.** What is the average total sales per year from 2019 to 2023?
= (300+300+400+500+600)/5 = 2100/5 = **₹420 Crores**

### 6.5 Pie Chart DI — Full Worked Example

**Budget Allocation of a Company (Total = ₹240 Crore)**

| Department | % Share |
|---|---|
| R&D | 25% |
| Marketing | 20% |
| Operations | 30% |
| HR | 10% |
| IT | 15% |

**Q1.** What is the amount allocated to Marketing and IT combined?
= (20+15)% of 240 = 35% of 240 = **₹84 Crore**

**Q2.** If R&D budget is increased by 20%, and total budget stays same, what % of budget does R&D now consume?
Old R&D = 25% of 240 = 60. New = 60×1.20 = 72.
% = 72/240×100 = **30%**

**Q3.** Operations spending exceeds HR spending by how much?
= (30−10)% of 240 = 20% of 240 = **₹48 Crore**

### 6.6 Line Graph DI — Full Worked Example

**Monthly Website Traffic (in thousands)**

| Month | Traffic |
|---|---|
| Jan | 50 |
| Feb | 65 |
| Mar | 80 |
| Apr | 60 |
| May | 90 |
| Jun | 120 |

**Q1.** Highest month-over-month growth?
Feb−Jan: 15, Mar−Feb: 15, Apr−Mar: −20, May−Apr: 30, Jun−May: 30
Percentage: Jan→Feb: 30%, Feb→Mar: 23%, Apr→May: 50%, May→Jun: 33.3%
**Answer: April to May (50%)**

**Q2.** Average monthly traffic?
= (50+65+80+60+90+120)/6 = 465/6 = **77.5 thousand**

**Q3.** In which month was traffic more than 20% above the average?
Average = 77.5. 20% above = 93.
Only June (120) > 93. **Answer: June**

### 6.7 DI Speed Strategy

**The 90-Second Rule for DI Clusters:**
- Spend 30−40 seconds understanding the data (don't solve yet)
- Identify what type of calculation each question needs
- Do the calculation mentally using approximation where possible
- Only write out full calculations for the one or two hardest sub-questions

**Key approximation trick:** For percentages, round to nearest 5%. So if actual is 23.7%, treat as 25% mentally to check if answer choices are in the right ballpark, then refine.

---

## 7. ADVANCED LOGICAL REASONING

### 7.1 Critical Reasoning — Argument Structure

**Parts of an Argument:**
- **Premise:** The fact/evidence given (what we know is true)
- **Conclusion:** What is being claimed based on the premises
- **Assumption:** The hidden premise that bridges fact to conclusion
- **Inference:** What logically follows from the premises

**Key Question Types:**

**Type 1 — Strengthen the Argument:**
Find the statement that makes the conclusion MORE likely to be true.
→ Eliminate options that are irrelevant. Pick the one that provides direct support.

**Type 2 — Weaken the Argument:**
Find the statement that makes the conclusion LESS likely to be true.
→ Look for an alternate explanation, or a fact that contradicts the premise.

**Type 3 — Identify the Assumption:**
The assumption is the unstated premise. The argument falls apart without it.
→ "Negate Test:" Negate each option. The one whose negation DESTROYS the argument = the assumption.

**Type 4 — Find the Conclusion:**
Among the statements, identify which one follows from the others.
→ The conclusion is usually more specific than the premises. It can't be used to derive the premises.

**Type 5 — Inference / Must Be True:**
A true inference is 100% guaranteed by the stated information — not probably true, not usually true. MUST be true.

### 7.2 Worked Examples — Critical Reasoning

**Example 1 (Assumption):**
"Students who use smartphones in class perform worse academically. Schools should ban smartphones."

Assumption being made:
(A) Smartphones are the cause of poor performance, not just correlated with it. ✅
(B) Academic performance is the only metric that matters
(C) All students use smartphones in class
(D) Schools have the authority to ban smartphones

**Negate Test on (A):** "Smartphones are NOT the cause of poor performance." → If this is true, banning them won't help → The argument falls apart. ✅

**Answer: A**

**Example 2 (Weaken):**
"City X reduced its crime rate after installing more street lights. Therefore, street lights reduce crime."

Which weakens this?
(A) Crime increased in neighboring City Y during the same period ✗ (irrelevant)
(B) City X also hired 200 more police officers during this period ✅ (alternate explanation — crime may have dropped due to police, not lights)
(C) Street lights cost a lot to install ✗ (irrelevant to whether they reduce crime)
(D) City X has a high population density ✗ (irrelevant)

**Answer: B**

**Example 3 (Strengthen):**
"Our new drug reduces cholesterol levels. It should be approved as a heart disease treatment."

Which strengthens this?
(A) High cholesterol is a primary cause of heart disease ✅ (directly links cholesterol to heart disease, validating the drug's relevance)
(B) The drug is affordable ✗ (doesn't strengthen medical effectiveness)
(C) Heart disease is the leading cause of death ✗ (doesn't connect cholesterol to heart disease)

**Answer: A**

### 7.3 Multi-Statement Logic Puzzles

**Type: Truth-Teller / Liar Problems**

**Setup:** Some people always tell truth (Knights), some always lie (Knaves). Determine who is who based on their statements.

**Rules:**
- If a Knight says "X is a Knight" → X is a Knight
- If a Knight says "X is a Knave" → X is a Knave
- If a Knave says "X is a Knight" → X is a Knave
- If a Knave says "X is a Knave" → X is a Knight

**Worked Example:**
A says: "Both of us are Knaves."
Can A be a Knight? If A is a Knight, then "both are Knaves" is true → A is also a Knave. Contradiction.
So A is a Knave. Then A's statement is false. "Both are Knaves" is false → B is NOT a Knave → B is a Knight.
**A = Knave, B = Knight**

**Type: Constraint Logic Problems**

Five friends (A,B,C,D,E) have different professions. Use clues to match each person to their profession.

**Method — Elimination Grid:**

| | Doctor | Engineer | Lawyer | Teacher | Banker |
|---|---|---|---|---|---|
| A | ? | ? | ? | ? | ? |
| B | ? | ? | ? | ? | ? |
| C | ? | ? | ? | ? | ? |
| D | ? | ? | ? | ? | ? |
| E | ? | ? | ? | ? | ? |

Mark ✅ when confirmed, ✗ when eliminated. A row with only one ? remaining = confirmed.

### 7.4 Advanced Arrangement (Multi-Variable)

**Double Row Arrangement:**
People in two rows facing each other. Questions about who faces whom, left/right relationships.

**Key Rule:**
If row 1 faces North and row 2 faces South:
- Person in row 1's left = West direction
- Person in row 2's left = East direction
- Person A in row 1 faces the person directly opposite in row 2

**Multi-Floor Arrangement:**
People on different floors of a building.
- Higher floor = greater floor number
- "X is immediately above Y" = X's floor = Y's floor + 1

**Multi-Parameter Puzzle (Most Complex):**
Assign multiple attributes (color, profession, nationality, pet) to multiple people (like Einstein's Riddle).

**Step-by-step method:**
1. Start with direct assignments (clue says "A likes Red")
2. Use those to derive more (if A=Red and Red is in position 1, then A is in position 1)
3. Eliminate systematically until all cells are filled

---

## 8. PROGRESSIONS & SERIES (ADVANCED)

### 8.1 Harmonic Progression (HP)

A sequence is HP if the reciprocals form an AP.
1/a, 1/(a+d), 1/(a+2d)...

**Harmonic Mean of a and b:**
HM = 2ab/(a+b)

**Relationship between AM, GM, HM:**
AM ≥ GM ≥ HM (equality when all numbers are equal)
GM² = AM × HM

**Example:** AM of two numbers = 10, GM = 8. Find HM.
HM = GM²/AM = 64/10 = **6.4**

### 8.2 Special Sums (Must Memorize)

**Sum of first n natural numbers:**
Σn = n(n+1)/2

**Sum of squares:**
Σn² = n(n+1)(2n+1)/6

**Sum of cubes:**
Σn³ = [n(n+1)/2]² = (Σn)²

**Sum of first n odd numbers:**
1+3+5+...+(2n−1) = n²

**Sum of first n even numbers:**
2+4+6+...+2n = n(n+1)

**Example:** Find 1²+2²+3²+...+20²
= 20×21×41/6 = **2870**

**Example:** Find 1³+2³+...+10³
= [10×11/2]² = 55² = **3025**

### 8.3 Infinite GP — Special Applications

Sum to infinity: S = a/(1−r) for |r| < 1

**Recurring Decimals as Fractions:**
0.333... = 3/9 = 1/3
0.142857... = 1/7
0.666... = 2/3
0.999... = 1

**General Method:**
0.abcabc... = abc/999
0.0abcabc... = abc/9990
0.a̅ = a/9
0.ab̅ (b repeating) = (ab−a)/90

**Example:** Convert 0.2̄7̄ (27 repeating) to fraction:
= 27/99 = **3/11**

**Example:** Convert 0.12̄ (2 repeating) to fraction:
= (12−1)/90 = 11/90 → **11/90**

### 8.4 Advanced AP-GP Hybrid

**AGP (Arithmetico-Geometric Progression):**
Terms: a, (a+d)r, (a+2d)r², (a+3d)r³...
Sum = ar/(1−r) + dr²/(1−r)² (for infinite series, |r|<1)

**Example:** Find 1 + 2×(1/2) + 3×(1/4) + 4×(1/8) + ...
S = 1/(1−1/2) + (1/2)×(1/2)/(1−1/2)²
= 2 + (1/4)/(1/4)
= 2 + 1 = **3**

### 8.5 Practice Problems — Progressions

**Q1.** If 5th term of HP is 1/10 and 11th term is 1/16, find the 13th term.
Reciprocals form AP: 5th term=10, 11th term=16.
d = (16−10)/6 = 1. 13th term of AP = 16+(2×1) = 18.
13th term of HP = **1/18**

**Q2.** Find the sum 1/(1×2) + 1/(2×3) + 1/(3×4) + ... + 1/(99×100)
Each term: 1/(n(n+1)) = 1/n − 1/(n+1) (partial fractions)
Sum = (1−1/2) + (1/2−1/3) + ... + (1/99−1/100) = 1 − 1/100 = **99/100**

**Q3.** Sum of all natural numbers from 1 to 100 that are NOT multiples of 3 or 5?
Total sum = 5050
Sum of multiples of 3: 3+6+...+99 = 3×(33×34/2) = 3×561 = 1683
Sum of multiples of 5: 5+10+...+100 = 5×(20×21/2) = 5×210 = 1050
Sum of multiples of 15: 15+30+...+90 = 15×(6×7/2) = 15×21 = 315
By inclusion-exclusion: 1683+1050−315 = 2418
Answer = 5050−2418 = **2632**

---

## 9. SET THEORY (ADVANCED)

### 9.1 Advanced Set Operations

**Laws:**
- De Morgan's: (A∪B)' = A'∩B' | (A∩B)' = A'∪B'
- Distributive: A∩(B∪C) = (A∩B)∪(A∩C)
- A−B = A∩B'
- |A−B| = |A| − |A∩B|
- |A Δ B| (Symmetric Difference) = |A|+|B|−2|A∩B|

### 9.2 Three-Set Advanced Problems

**Formula:**
n(A∪B∪C) = n(A)+n(B)+n(C) − n(A∩B) − n(B∩C) − n(A∩C) + n(A∩B∩C)

**Region breakdown (7 regions):**
- Only A = n(A) − n(A∩B) − n(A∩C) + n(A∩B∩C)
- Only A and B (not C) = n(A∩B) − n(A∩B∩C)
- All three = n(A∩B∩C)

### 9.3 Practice Problem

In a survey of 200 people about languages spoken:
- English (E): 120
- Hindi (H): 100
- Tamil (T): 80
- E and H: 50
- H and T: 40
- E and T: 30
- All three: 20

**Q1.** How many speak at least one language?
= 120+100+80−50−40−30+20 = **200** (all surveyed)

**Q2.** How many speak only English?
= 120−50−30+20 = **60**

**Q3.** How many speak exactly two languages?
= (E∩H only) + (H∩T only) + (E∩T only)
= (50−20) + (40−20) + (30−20)
= 30+20+10 = **60**

**Q4.** How many speak exactly one language?
= Only E + Only H + Only T
Only E = 120−50−30+20 = 60
Only H = 100−50−40+20 = 30
Only T = 80−40−30+20 = 30
Total = **120**

---

## 10. INEQUALITIES & MODULAR ARITHMETIC

### 10.1 Inequalities — Key Rules

**Basic Rules:**
- If a > b and c > 0: ac > bc (inequality direction preserved)
- If a > b and c < 0: ac < bc (inequality direction REVERSES)
- If a > b and p > q (same sign): a+p > b+q
- a² > b² does NOT imply a > b (consider negative numbers)

**Absolute Value Inequalities:**
- |x| < a ↔ −a < x < a
- |x| > a ↔ x < −a OR x > a
- |x − k| < d ↔ k−d < x < k+d (x is within distance d from k)

**Example:** Solve |2x−3| ≤ 5
−5 ≤ 2x−3 ≤ 5
−2 ≤ 2x ≤ 8
**−1 ≤ x ≤ 4**

**AM-GM Inequality:**
For positive numbers: (a+b)/2 ≥ √(ab)
Equality when a = b.

**Application:** If a+b=10, maximum value of ab?
ab ≤ [(a+b)/2]² = 25. Equality when a=b=5. **Max ab = 25**

**If ab=36, minimum value of a+b (positive a,b)?**
a+b ≥ 2√(ab) = 2×6 = 12. **Min a+b = 12** when a=b=6.

### 10.2 Modular Arithmetic

**x ≡ a (mod n)** means x leaves remainder a when divided by n.

**Operations:**
- (a+b) mod n = [(a mod n) + (b mod n)] mod n
- (a×b) mod n = [(a mod n) × (b mod n)] mod n
- (a−b) mod n = [(a mod n) − (b mod n) + n] mod n

**Example:** (17 × 23 − 8) mod 5
= [(17 mod 5) × (23 mod 5) − (8 mod 5)] mod 5
= [2 × 3 − 3] mod 5
= [6 − 3] mod 5
= 3 mod 5 = **3**

**Congruence Applications:**
Find last digit of 1! + 2! + 3! + ... + 100!
Note: n! for n≥10 ends in 0 (contains factors 2 and 5 multiple times)
Sum of last digits = 1+2+6+24+120+720+5040+40320+362880+... 
= 1+2+6+4+0+0+0+0+0+0+... = **3** (last digit)

---

## 11. MATRICES & DETERMINANTS

### 11.1 Matrix Basics

**Types:**
- Square matrix: n×n
- Identity matrix I: diagonal = 1, rest = 0
- Zero matrix: all elements = 0
- Diagonal matrix: off-diagonal = 0
- Symmetric: A = Aᵀ | Skew-symmetric: A = −Aᵀ

**Matrix Multiplication:**
For A(m×n) and B(n×p): Product C = A×B is (m×p)
Cᵢⱼ = Σ (row i of A) × (column j of B)

### 11.2 Determinant of 2×2 Matrix

|a b|
|c d| = ad − bc

**For 3×3 Matrix:**
|a b c|
|d e f| = a(ei−fh) − b(di−fg) + c(dh−eg)
|g h i|

**Properties:**
- det(AB) = det(A) × det(B)
- det(Aᵀ) = det(A)
- det(kA) = kⁿ det(A) for n×n matrix
- If two rows/columns are identical: det = 0
- Swapping two rows/columns: det changes sign

**Singular Matrix:** det = 0 (no inverse exists)

### 11.3 Matrix Inverse (2×2)

For A = |a b|, A⁻¹ = 1/(ad−bc) × |d −b|
         |c d|                        |−c  a|

**Example:**
A = |2 3|, det = 2×4−3×1 = 5
    |1 4|

A⁻¹ = 1/5 × |4 −3| = |0.8  −0.6|
              |−1  2|   |−0.2  0.4|

### 11.4 Practice Problems — Matrices

**Q1.** Find det |3 2 1|
                 |0 4 2|
                 |1 3 2|

= 3(4×2−2×3) − 2(0×2−2×1) + 1(0×3−4×1)
= 3(8−6) − 2(0−2) + 1(0−4)
= 3(2) − 2(−2) + 1(−4)
= 6 + 4 − 4 = **6**

**Q2.** If A = |1 2| and B = |2 0|, find AB.
              |3 4|          |1 3|

AB = |1×2+2×1  1×0+2×3| = |4  6|
     |3×2+4×1  3×0+4×3|   |10 12|

---

## 12. ADVANCED PUZZLES & CRITICAL REASONING

### 12.1 The Grid Puzzle (Einstein's Riddle Type)

**Framework:**
5 attributes × 5 positions. Given ~15 clues, find the unique solution.

**General Solving Strategy:**
1. Apply direct clues first (X is in position 3)
2. Apply adjacent/sequential clues
3. Eliminate impossible combinations
4. Use "if...then" chains
5. When stuck, hypothesize one assignment and see if it leads to contradiction

### 12.2 Weighing Puzzles

**Classic:** 12 balls, one is different weight (heavier or lighter unknown). Find it in 3 weighings.

**Strategy:** In each weighing, split into 3 groups (left pan, right pan, aside). Each weighing gives 3 outcomes (left heavy, right heavy, balanced). 3 weighings → 3³=27 possible outcomes → can solve up to 27-object problems.

**General Rule:** n weighings can identify the odd ball among (3ⁿ−3)/2 balls if you know heavier/lighter, or (3ⁿ−3)/2 if unknown.

### 12.3 River Crossing Puzzles

**Classic setup:** Get all people/objects across with constraints.
**Method:** List each state as (left bank, right bank, boat position). Use BFS (breadth-first search mentally) to find shortest sequence.

### 12.4 Advanced Arrangement Puzzles — Worked Example

**Seven people A,B,C,D,E,F,G are seated in a straight row facing North.**

Clues:
1. A is 3rd from the left
2. F is to the immediate right of E
3. B and D have exactly 2 people between them
4. G is at one of the ends
5. C is between A and F
6. D is not adjacent to A

**Solve:**
From clue 1: _ _ A _ _ _ _
From clue 5: C is between A and F. So either A_C_F or F_C_A (C between them)
From clue 2: F is immediately right of E → E F are consecutive
Combining: if F is to the right of C which is to the right of A: A _ C _ E F _ or _ A C E F _ _

Try: positions 1−7
A=3. C is between A and F, F must be to the right of E (EF consecutive).
If C=4, E=5, F=6: valid (A=3, C=4, E=5, F=6)
Remaining: B,D,G for positions 1,2,7
From clue 4: G at one end → G=1 or G=7
From clue 3: B and D have exactly 2 people between them → |B_pos − D_pos| = 3
Positions available: 1,2,7 for B,D,G.
|2−? |=3: not possible within {1,2,7}. Actually we only have 3 people for 3 spots.
Pairs from {1,2,7}: |1−2|=1, |1−7|=6, |2−7|=5. None = 3. Contradiction.

Try C=5: A=3, C=5. E,F are consecutive. F must be to the right of C(5): E=6,F=7 or E=5 (conflict with C).
If E=6, F=7: Remaining: B,D,G for positions 1,2,4.
G at end: G=1 (end) or G=7(F already there). So G=1.
B,D for positions 2,4. |2−4|=2 ≠ 3. Contradiction.

Try C=2: A=3, C=2. F to the right of C → F=4,5,6,7. EF consecutive with F>E.
E=4,F=5 or E=5,F=6 or E=6,F=7.
If E=4,F=5: Remaining: B,D,G for 1,6,7. G at end: G=1 or G=7.
D not adjacent to A(3): D≠2(C's),D≠4(E's). D ∈ {1,6,7}.
B and D: |B−D|=3. From {1,6,7}: |1−7|=6,|1−6|=5,|6−7|=1. None=3. Contradiction.

If E=5,F=6: Remaining: B,D,G for 1,4,7. G=1 or G=7.
|B−D|=3. From {1,4,7}: |1−4|=3 ✅ or |4−7|=3 ✅.
D not adjacent to A(3): D≠2,D≠4. So D∈{1,7}.
If D=1, B=4: D not adjacent to A(3)? |1−3|=2, not adjacent ✅. G=7.
Final: G,D,A,B,C,E,F → **G D A B C E F** — but check clue 3: |B(4)−D(1)|=3 ✅

**Answer: G D A B C E F** ✅

---

## 13. ADVANCED CLOCK & CALENDAR

### 13.1 Clock — Advanced Problems

**Mirrors and Clock:**
If a clock shows time T in a mirror, actual time = 11:60 − T (or 12:00 − T, adjust for exact hour)

Example: Mirror shows 8:20. Actual time = 11:60−8:20 = **3:40**

**Clock gaining/losing time:**
If a clock gains G minutes per hour, in T hours it shows T hours + T×G minutes extra.

If clock gains 5 minutes per hour, what time does it show after 10 actual hours if set correctly at noon?
Extra = 10×5 = 50 minutes. Shows 10 hours 50 minutes → **10:50 PM**

**Between two times, how many times do hands coincide?**
In 12 hours: 11 times. In 24 hours: 22 times.
Between specific times: divide the 11 coincidences evenly across 12 hours.

### 13.2 Calendar — Advanced

**Day of any date formula (Zeller's/Standard):**
For quick computation, use odd-days method and anchor dates.

**Anchor dates (memorize):**
- 1/1/2000 = Saturday
- 1/1/2023 = Sunday
- 1/1/2024 = Monday
- 1/1/2025 = Wednesday

**Leap year rules:**
- Divisible by 4: leap year (usually)
- Divisible by 100: NOT a leap year
- Divisible by 400: IS a leap year

So: 2000=leap✅, 1900=not leap✅, 2100=not leap, 2400=leap

**Finding day given anchor:**
From anchor date, count odd days to target date.
Each ordinary year = 1 odd day. Each leap year = 2 odd days.

**Example:** January 1, 2025 = Wednesday. What day is March 15, 2025?
Jan has 31 days. From Jan 1 to Mar 15:
Remaining January: 30 days. February 2025: 28 days. 14 days in March.
Total days from Jan 1 = 30+28+14 = 72 days.
72 = 10 weeks + 2 days. Wednesday + 2 = **Friday**

---

## 14. MISCELLANEOUS HIGH-ORDER PROBLEMS

### 14.1 Maxima-Minima Word Problems

**Classic Type:** Maximize area given fixed perimeter, or minimize perimeter given fixed area.

**Key results to remember:**
- Among all rectangles with same perimeter: **square has maximum area**
- Among all shapes with same perimeter: **circle has maximum area**
- For a rectangle: if perimeter = 2(l+b), max area = when l=b (square)

**Example:** A farmer has 200m of fencing. What is the maximum area he can enclose?
If square: side = 50m, area = 2500m²
If rectangle (not square): always less than 2500m²
**Maximum area = 2500m²**

**Example (three sides):** One side uses a wall. Maximize area with 120m of fencing for 3 sides.
Let width = w (two sides), length = l (one side). 2w+l=120 → l=120−2w
Area = l×w = w(120−2w) = 120w−2w²
dA/dw = 120−4w = 0 → w=30, l=60
**Maximum area = 30×60 = 1800m²**

### 14.2 Mixture & Alligation (Advanced)

**Rule of Alligation:**
When two ingredients at prices C₁ and C₂ are mixed to get mean price Cm:
Ratio = (C₂−Cm) : (Cm−C₁)

**Advanced: Three-component mixture:**
A mixture of 3 things can be solved by applying alligation twice.

**Replacement Problems:**
If a vessel has x litres of liquid A and y litres of liquid B, and we repeatedly remove k litres and replace with B:
After n replacements: Amount of A = x × [(x−k)/x]ⁿ... wait:
Total volume is x+y. After n replacements:
Amount of A remaining = (Total) × [(x−k)/(x+y−k+y)]ⁿ... 

Actually the standard formula:
A vessel of volume V has pure A. Each time k litres removed and replaced with B.
After n operations: Amount of A = V × [(V−k)/V]ⁿ

**Example:** 40L vessel of milk. 5L removed and replaced with water, 3 times.
Milk remaining = 40 × (35/40)³ = 40 × (7/8)³ = 40 × 343/512 = **26.8 litres**

### 14.3 Work & Time (Advanced)

**Pipes with Variable Rates:**
Some pipes fill at different rates at different times.

**Work Done in Parts:**
If A does x part of work and B does remaining:
A:B in work = x:(1−x)
A:B in time = (1−x)/T_A : x/T_B

**Efficiency Problems:**
If wages are divided in ratio of work done and A and B work for different days:
Wage ratio = Days_A × Rate_A : Days_B × Rate_B

**Example:** A can do a job in 12 days, B in 18 days, C in 9 days. All start together. A leaves after 3 days, B leaves 3 days before completion. How many days total?
LCM(12,18,9) = 36. A=3/day, B=2/day, C=4/day.
Let total days = T.
Work done: A works 3 days: 9 units. C works T days: 4T units. B works (T−3) days: 2(T−3) units.
Total = 36: 9 + 4T + 2(T−3) = 36
9 + 4T + 2T − 6 = 36
6T + 3 = 36
6T = 33 → T = 5.5 → **T = 5.5 days**

---

## 📅 TOPIC-WISE WEIGHTAGE — ADVANCED QR

| Topic | Expected Questions | Difficulty |
|---|---|---|
| Data Interpretation | 5−6 | Medium-High |
| Advanced Algebra & Functions | 3−4 | High |
| Advanced P&C & Probability | 3−4 | High |
| Number Theory | 2−3 | High |
| Advanced Puzzles & Arrangements | 2−3 | Very High |
| Geometry & Coordinate | 2−3 | High |
| Progressions & Series | 1−2 | Medium-High |
| Critical Reasoning | 1−2 | High |
| Inequalities & Modular | 1−2 | Medium |
| Matrices | 1 | Medium |

---

## ⚡ PRIME PACKAGE PERFORMANCE SHORTCUTS

### Speed Math for Advanced Level

**Fast Square Roots (Approximation):**
√2 = 1.414 | √3 = 1.732 | √5 = 2.236 | √6 = 2.449 | √7 = 2.646 | √10 = 3.162

**Fast Cube Roots:**
∛2 = 1.26 | ∛3 = 1.44 | ∛4 = 1.587 | ∛5 = 1.71

**Power of 2 (Memorize up to 2^15):**
2^1=2, 2^2=4, 2^3=8, 2^4=16, 2^5=32, 2^6=64, 2^7=128, 2^8=256, 2^9=512, 2^10=1024
2^11=2048, 2^12=4096, 2^13=8192, 2^14=16384, 2^15=32768

**Key Factorials:**
1!=1, 2!=2, 3!=6, 4!=24, 5!=120, 6!=720, 7!=5040, 8!=40320, 9!=362880, 10!=3628800

**Percentage Shortcuts:**
- 1% of X = X/100 (move decimal 2 places left)
- 10% = X/10
- To find 35%: find 30% + 5% = 3(10%) + half(10%)
- To find 125% of X: X + 25% of X = X + X/4 = 5X/4

### Error Avoidance in Exam

**Top 10 Traps TCS Sets:**

1. "At least one" vs "exactly one" — completely different
2. Inclusive vs Exclusive counting ("between 5 and 10" = 4 or 6 numbers?)
3. Percentage OF vs Percentage MORE THAN (20% more than 100 = 120, NOT 20)
4. Sum of digits vs Number itself (digits of 123 are 1,2,3 not 123)
5. Simple Interest vs Compound Interest — read carefully
6. "From start" vs "From end" in sequences
7. Circular arrangement: (n−1)! not n!
8. "Both can" vs "at least one can" in probability
9. LCM vs HCF — choosing wrong one
10. The word "approximately" — when given, use estimation, don't calculate exactly

---

## 🎯 EXAM-DAY STRATEGY FOR PRIME PACKAGE

### The Prime Candidate's Time Budget (25 min, 25 questions)

| Time Slot | Action |
|---|---|
| 0:00−0:30 | Scan all 25 questions. Categorize: Easy/Medium/Hard |
| 0:30−8:00 | Solve all Easy questions first (Series, basic algebra, DI reading) |
| 8:00−18:00 | Solve Medium questions (DI calculations, P&C, probability) |
| 18:00−24:00 | Attempt Hard questions (Puzzles, critical reasoning) |
| 24:00−25:00 | Guess remaining unattempted (mark most common option C if TCS has no negative marking) |

### Scoring Target for Prime Package

TCS doesn't officially publish cutoffs, but based on selections:
- Part A (75 marks): Target **70+ correct** (~93%)
- Advanced QR (25 marks): Target **18+ correct** (72%+)
- Advanced Coding: Target **both questions attempted with at least one fully correct**

To get Prime, you need to be in the **top 10% of all candidates.** That means your accuracy must be dramatically higher than average in both Part A and Part B.

### The Mental Framework of a Prime Candidate

Every question you see, ask yourself in order:
1. **What type is this?** (Identify the concept in 5 seconds)
2. **What's the fastest method?** (Formula? Elimination? Approximation?)
3. **What are common mistakes here?** (Sign errors? Wrong formula variant?)
4. **What's my answer and which option matches?**

If after 60 seconds you don't have an answer, **skip and mark for review.** Never sacrifice 3 future questions for 1 current question.

### The Prime Package Mindset

The difference between a Prime package and a Ninja package isn't intelligence. It's **preparation depth + composure under pressure.**

You have now studied:
- Every Numerical formula and shortcut
- Every Verbal grammar rule and vocabulary group
- Every Reasoning pattern and method
- Every Advanced QR concept including DI, Number Theory, Algebra, Geometry, P&C, Probability, Matrices, Progressions, Critical Reasoning, and Puzzles

**What remains is execution.** Practice 30−40 questions daily under timed conditions. Simulate the actual exam once a week (190 minutes, full paper, no breaks, no interruptions).

The next section — **Advanced Coding (90 minutes)** — will require a completely different kind of preparation. That's where we go next, whenever you're ready.

This is your moment. Now go claim it. 🔥💪
