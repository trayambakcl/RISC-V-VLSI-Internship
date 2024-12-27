# RISC-V-VLSI-Internship
Wrote a simple c code and executed it using the gcc compiler to find the sum of integers till n
```c
#include <stdio.h>
        int main() {
            int i, sum = 0, n = 60;
            for (i = 1; i <= n; ++i) {
                sum += i;
            }
            printf("Sum of number from 1 to %d is %d\n", n, sum);
            return 0;
        }
```
        
<img width="960" alt="Screenshot 2024-12-22 202824" src="https://github.com/user-attachments/assets/55b37e90-9667-4d60-b122-dd7f7f9b53aa" />

disassembled using the O1 method
<img width="960" alt="2" src="https://github.com/user-attachments/assets/cfab1604-09aa-4630-be86-b04450bc98dc" />

disassembled using the Ofast method
<img width="956" alt="3" src="https://github.com/user-attachments/assets/0e8dd756-2828-4994-afaa-eec0cb063ea1" />


In both of the above steps, the number of instructions for the code were found.
The second('Ofast') method has lesser instructions.
