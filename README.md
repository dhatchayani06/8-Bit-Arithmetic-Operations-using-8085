# 8-Bit-Arithmetic-Operations-using-8085
## Aim:
To perform 8-bit arithmetic operations such as addition, subtraction, multiplication, and division using the 8085 microprocessor.

## Apparatus Required:
•	Laptop with internet connection

## Algorithm:

### For Addition (With Carry Consideration):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Add the contents of registers A and B.
4.	If carry is generated, store carry in 4301H.
5.	Store the sum in memory location 4300H.
   
### Program:
```
LDA 4200H
MOV B,A
LDA 4201H
ADD B
STA 4300H
JC STORE_CARRY
HLT
STORE_CARRY:MVI A,01H
STA 4301H
HLT
```

<img width="1919" height="1010" alt="Screenshot 2025-08-28 100600" src="https://github.com/user-attachments/assets/f9108cbc-7854-4805-8dfe-898333ca80da" />


### Output:
<img width="1917" height="1199" alt="Screenshot 2025-08-28 100401" src="https://github.com/user-attachments/assets/9bfd8aa6-aa9e-4b88-9ab4-aae1d70b2781" />


### For Subtraction (Considering Greater Number):
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Compare A and B.
4.	If A < B, swap the values of A and B to ensure positive result.
5.	Subtract the content of B from A.
6.	Store the result in memory location 4300H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
CMP C
JC SWAP
MOV B,A
MOV A,C
SWAP: SUB B
STA 4300H
HLT
```
<img width="1912" height="1037" alt="Screenshot 2025-08-28 101618" src="https://github.com/user-attachments/assets/a4729d2d-410c-4ae5-bcb2-4bfd4746a5fd" />


### Output:
<img width="1914" height="952" alt="Screenshot 2025-08-28 101634" src="https://github.com/user-attachments/assets/be9ad2b8-2133-466f-8af5-805541cca97e" />


### For Multiplication:
1.	Load the first number from memory location 4200H into register A.
2.	Load the second number from memory location 4201H into register B.
3.	Multiply A and B using repeated addition.
4.	Store the result in memory locations 4300H and 4301H (if required for higher bits).

### Program:
```
LDA 4200H
MOV C, A
LDA 4201H
MOV B,A
MVI A, 00H
LOOP: ADD C
DCR B
JNZ LOOP
STA 4300H
HLT
```
<img width="1908" height="983" alt="Screenshot 2025-08-28 102550" src="https://github.com/user-attachments/assets/6c9b038c-d32a-4ad0-84e6-efa9df5500d6" />


### Output:
<img width="698" height="479" alt="Screenshot 2025-08-28 102610" src="https://github.com/user-attachments/assets/fdffa432-95ec-4151-a151-143bd2f80813" />


### For Division:
1.	Load the dividend from memory location 4200H into register A.
2.	Load the divisor from memory location 4201H into register B.
3.	Perform division using repeated subtraction.
4.	Store the quotient in 4300H and remainder in 4301H.

### Program:
```
LDA 4200H
MOV C,A
LDA 4201H
MOV B, A
MVI A, 00H
LOOP: MOV A,C
CMP B
JC END
SUB B
MOV C, A
INR D
JMP LOOP
END: MOV A, D
STA 4300H
MOV A, C
STA 4301H
HLT
```
<img width="1896" height="965" alt="Screenshot 2025-08-28 103221" src="https://github.com/user-attachments/assets/4f030485-9285-4dc0-af6c-c220223622aa" />

### Output:
<img width="1826" height="1029" alt="Screenshot 2025-08-28 103245" src="https://github.com/user-attachments/assets/d0e8246d-0f26-4776-8e5d-ad50420c73b8" />


## Result:
The 8-bit arithmetic operations using the 8085 microprocessor have been successfully executed and verified using memory access for input and output.

