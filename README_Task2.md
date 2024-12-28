# DEBUGGING USING SPIKE COMMAND
## using the previously made c code

   
The instruction set (Object Dump) is given below.

<img width="959" alt="3" src="https://github.com/user-attachments/assets/28cdc27f-106a-4d35-b3ba-be5f8e684283" />


img width="476" alt="4" src="https://github.com/user-attachments/assets/20478d2e-47ba-421f-8e78-a6fa5cba1795" />


 ## The  **main** starts from hexadecimal  value 100b0 in assembly language followed by several other commands.

   
 To start debugging we run the command 
 
         spike -d pk sum1ton.o 
 

 ## The program counter (pc) was run till a certain instruction(100b0) and it was manually run after that for debugging. 
##   Each instruction was run by clicking enter each time.

          until pc 0 100b0

runs at core 0 from beginning to 100b0
## We the use the command 
          reg 0 a2

 to see the contents we use the given register
#### NOTE : LUI stands for Load Upper Immediate.  

## To see the content of the reg
<img width="960" alt="5" src="https://github.com/user-attachments/assets/c9717188-eb33-4259-8898-0fbe4b92300a" />

## After that if we press enter it will move onto next set of instruction
<img width="660" alt="newnew2" src="https://github.com/user-attachments/assets/d5ea5536-d14f-478b-b0c8-839c95d2cf7a" />


again to check the contents we use the command.

          reg 0 sp

#### sp stands for the stack pointer the stack is like a special memory storage where the computer keeps track of temporary data , the decimal -16 means that the content in sp got upadted to 10 in hexadecimal 
          


##      hit q to quit and the run the command again :  
The contents of the Stack Pointer(SP) register was observed. The stack pointer register(SP) instruction was run and the contents of the SP were looked at again.


           spike -d pk sum1ton.o




## Then we use the command 
      reg 0 sp

 <img width="630" alt="newnew3" src="https://github.com/user-attachments/assets/dd532831-16a6-4a32-b27d-29ebf80ac8d0" />

then one can notice that the value got reduced by 10 hexadecimal or by 16 in decimal

#### NOTE :  addi stands for add immediate it’s an instruction in the RISC-V assembly language that adds a constant number to a register.

## compiled  c code for fiding fibonacci sequence upto n terms
<img width="827" alt="Screenshot 2024-12-27 214341" src="https://github.com/user-attachments/assets/0648e912-d5d8-42f3-9a37-17c620060d0f" />
```


#include <stdio.h>

void printFibonacci(int n) {
    int first = 0, second = 1, next;

    if (n < 1) {
        printf("Please enter a positive integer.\n");
        return;
    }

    printf("Fibonacci Sequence for %d terms:\n", n);

    for (int i = 1; i <= n; i++) {
        if (i == 1) {
            printf("%d ", first);
            continue;
        }
        if (i == 2) {
            printf("%d ", second);
            continue;
        }
        next = first + second;
        first = second;
        second = next;
        printf("%d ", next);
    }
    printf("\n");
}

int main() {
    int n;

    printf("Enter the number of terms in the Fibonacci sequence: ");
    scanf("%d", &n);

    printFibonacci(n);

    return 0;
}


```






              
