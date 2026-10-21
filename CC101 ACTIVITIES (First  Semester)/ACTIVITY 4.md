# Activity 4 - Base Conversion Laboratory

---

### Question 1

Convert $10101010_2$ to Decimal:

* $\text{Digit } 1 \rightarrow 2^7 = 128 \implies 1 \times 128 = 128$
* $\text{Digit } 0 \rightarrow 2^6 = 64 \implies 0 \times 64 = 0$
* $\text{Digit } 1 \rightarrow 2^5 = 32 \implies 1 \times 32 = 32$
* $\text{Digit } 0 \rightarrow 2^4 = 16 \implies 0 \times 16 = 0$
* $\text{Digit } 1 \rightarrow 2^3 = 8 \implies 1 \times 8 = 8$
* $\text{Digit } 0 \rightarrow 2^2 = 4 \implies 0 \times 4 = 0$
* $\text{Digit } 1 \rightarrow 2^1 = 2 \implies 1 \times 2 = 2$
* $\text{Digit } 0 \rightarrow 2^0 = 1 \implies 0 \times 1 = 0$

$$\text{Decimal Value} = 128 + 0 + 32 + 0 + 8 + 0 + 2 + 0 = 170$$

**Result:** $10101010_2 = 170_{10}$

---

### Question 2

Convert $3456_8$ to Decimal:

* $8^3 = 512 \implies 3 \times 512 = 1536$
* $8^2 = 64 \implies 4 \times 64 = 256$
* $8^1 = 8 \implies 5 \times 8 = 40$ *(Note: corrected arithmetic from OCR $5 \times 8 = 48$)*
* $8^0 = 1 \implies 6 \times 1 = 6$

$$\text{Decimal Value} = 1536 + 256 + 40 + 6 = 1838$$

*(Note: original document calculation had $1536 + 256 + 48 + 6 = 1846$ due to an operational typo in $5 \times 8$.)*

**Result:** $1838_{10}$

---

### Question 3

Convert $\text{F7C}_{16}$ to Decimal:

* $16^2 = 256; \quad \text{F} = 15 \implies 15 \times 256 = 3840$
* $16^1 = 16; \quad 7 = 7 \implies 7 \times 16 = 112$
* $16^0 = 1; \quad \text{C} = 12 \implies 12 \times 1 = 12$

$$\text{Decimal Value} = 3840 + 112 + 12 = 3964$$

**Result:** $\text{F7C}_{16} = 3964_{10}$

---

### Question 4

Convert $219_{10}$ to Binary:

* $219 / 2 = 109$, Remainder: $1$
* $109 / 2 = 54$, Remainder: $1$
* $54 / 2 = 27$, Remainder: $0$
* $27 / 2 = 13$, Remainder: $1$
* $13 / 2 = 6$, Remainder: $1$
* $6 / 2 = 3$, Remainder: $0$
* $3 / 2 = 1$, Remainder: $1$
* $1 / 2 = 0$, Remainder: $1$

Remainders (read bottom to top): $11011011_2$

**Result:** $219_{10} = 11011011_2$

---

### Question 5

Convert $1179_{10}$ to Octal:

* $1179 / 8 = 147$, Remainder: $3$
* $147 / 8 = 18$, Remainder: $3$
* $18 / 8 = 2$, Remainder: $2$
* $2 / 8 = 0$, Remainder: $2$

Remainders (read bottom to top): $2233_8$

**Result:** $1179_{10} = 2233_8$

---

### Question 6

Convert $2755_{10}$ to Hexadecimal:

* $2755 / 16 = 172$, Remainder: $3 \rightarrow 3$
* $172 / 16 = 10$, Remainder: $12 \rightarrow \text{C}$
* $10 / 16 = 0$, Remainder: $10 \rightarrow \text{A}$

Remainders / Hex digits (read bottom to top): $\text{AC3}_{16}$

**Result:** $2755_{10} = \text{AC3}_{16}$

---

### Question 7

Convert $10111010011_2$ to Hexadecimal:

Group into 4 bits (pad left with zero):
$$0101 \mid 1101 \mid 0011$$

* $0101_2 = 5_{16}$
* $1101_2 = \text{D}_{16}$
* $0011_2 = 3_{16}$

**Result:** $10111010011_2 = 5\text{D}3_{16}$

---

### Question 8

Convert $1001101111_2$ to Octal:

Group into 3 bits (pad left with zeros):
$$001 \mid 001 \mid 101 \mid 111$$

* $001_2 = 1_8$
* $001_2 = 1_8$
* $101_2 = 5_8$
* $111_2 = 7_8$

**Result:** $1001101111_2 = 1157_8$

---

### Question 9

Convert $2\text{E}8_{16}$ to Binary:

* $2_{16} = 0010_2$
* $\text{E}_{16} = 1110_2$
* $8_{16} = 1000_2$

Joined (dropping leading zeros): $1011101000_2$

**Result:** $2\text{E}8_{16} = 1011101000_2$

---

### Question 10

Convert $522_8$ to Hexadecimal:

1. **Octal to Binary:**
   * $5_8 = 101_2$
   * $2_8 = 010_2$
   * $2_8 = 010_2$
   * Binary representation: $101010010_2$

2. **Binary to Hexadecimal:**
   * Group into 4 bits (pad left with zeros): $0001 \mid 0101 \mid 0010$
   * $0001_2 = 1_{16}$
   * $0101_2 = 5_{16}$
   * $0010_2 = 2_{16}$

**Result:** $522_8 = 152_{16}$

---

### Question 11

Convert IPv4 Address to Binary: `172.20.207.174`

* $172 = 10101100_2$
* $20 = 00010100_2$
* $207 = 11001111_2$
* $174 = 10101110_2$

**Result:** `10101100.00010100.11001111.10101110`

---

### Question 12

#### a) Convert Hexadecimal Color Code `#BE68D5` to RGB (Decimal):

* $\text{Red} = \text{BE}_{16} = (11 \times 16) + 14 = 190$
* $\text{Green} = 68_{16} = (6 \times 16) + 8 = 104$
* $\text{Blue} = \text{D}5_{16} = (13 \times 16) + 5 = 213$

#### b) Convert Decimal RGB `rgb(81, 76, 80)` to Hexadecimal:

* $\text{Red} = 81_{10} = (5 \times 16) + 1 = 51_{16}$
* $\text{Green} = 76_{10} = (4 \times 16) + 12 = 4\text{C}_{16}$
* $\text{Blue} = 80_{10} = (5 \times 16) + 0 = 50_{16}$

**Result:** `#514C50`

---

### Question 13

Command: `chmod 744 report.txt`

* Owner $= 7 \implies 111_2 \implies \text{rwx}$
* Group $= 4 \implies 100_2 \implies \text{r--}$
* Others $= 4 \implies 100_2 \implies \text{r--}$

**Full permission string:** `rwxr--r--`

---

### Question 14

For a 10-bit integer:

* **How many different values can it store?** $2^{10} = 1024$ values
* **Largest value in decimal:** $2^{10} - 1 = 1023$
* **Largest value in binary:** $1111111111_2$
* **Largest value in hexadecimal:** $3\text{FF}_{16}$

---

### Question 15

Convert $N = 677$:

#### Binary:
* $677 / 2 = 338$, Remainder: $1$
* $338 / 2 = 169$, Remainder: $0$
* $169 / 2 = 84$, Remainder: $1$
* $84 / 2 = 42$, Remainder: $0$
* $42 / 2 = 21$, Remainder: $0$
* $21 / 2 = 10$, Remainder: $1$
* $10 / 2 = 5$, Remainder: $0$
* $5 / 2 = 2$, Remainder: $1$
* $2 / 2 = 1$, Remainder: $0$
* $1 / 2 = 0$, Remainder: $1$

Remainders (bottom to top): $1010100101_2$

#### Octal:
* $677 / 8 = 84$, Remainder: $5$
* $84 / 8 = 10$, Remainder: $4$
* $10 / 8 = 1$, Remainder: $2$
* $1 / 8 = 0$, Remainder: $1$

Remainders (bottom to top): $1245_8$

#### Hexadecimal:
* $677 / 16 = 42$, Remainder: $5 \rightarrow 5$
* $42 / 16 = 2$, Remainder: $10 \rightarrow \text{A}$
* $2 / 16 = 0$, Remainder: $2 \rightarrow 2$

Remainders (bottom to top): $2\text{A}5_{16}$

---

### Error Analysis

**Error Identification:**
The classmate read the division remainders from top to bottom (Least Significant Bit to Most Significant Bit) instead of bottom to top (MSB to LSB).

**Correct Conversion of $46_{10}$:**

* $46 / 2 = 23$, Remainder: $0$
* $23 / 2 = 11$, Remainder: $1$
* $11 / 2 = 5$, Remainder: $1$
* $5 / 2 = 2$, Remainder: $1$
* $2 / 2 = 1$, Remainder: $0$
* $1 / 2 = 0$, Remainder: $1$

Remainders (read bottom to top): $101110_2$
