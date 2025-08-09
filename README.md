# AdaptativeFilter-DSK6713
Adaptative Filter Algorithm implemented in assembly language for DSK6713 development board

The LMS adaptive filter algorithm is coded in assembly language in the Code Composer Studio IDE and implemented on the DSK6713 development board to analyze its behavior and optimization.
The operating principle of an adaptive filter is based on an adjustment algorithm that modifies its coefficients to minimize an error function. Given a system with an input signal $x(n)$ and a desired output $d(n)$, the adaptive filter generates an estimated output $y(n)$, then the error is defined as:

$e(n)=d(n)-y(n)$

In general, an adaptive filter can be implemented based on an FIR filter with the characteristic that the coefficients are self-adjusting, resulting in the following equation that defines it:

$y(n)=\sum_{k=0}^{N-1} w_k(n)x(n-k)$
## Design and implementation
Based on the equations for both error calculation and the self-adjusting coefficient filter model, by developing it using mathematical methods and applying the concept of descending gradient, the calculation of the coefficients can be defined as:

$w_k (n+1)=w_k (n)+μe(n)x(n-k)$

Based on this, adaptive LMS filters can be implemented for:
* Noise cancellation
  
  <img width="492" height="191" alt="image" src="https://github.com/user-attachments/assets/50a3551d-11b3-4f5f-9a0d-a94888e200f2" />

* System recognition
  
<img width="577" height="231" alt="image" src="https://github.com/user-attachments/assets/b4e87400-b9b8-45e1-8732-9784b86372f5" />

* Adaptive prediction
  
<img width="560" height="259" alt="image" src="https://github.com/user-attachments/assets/2921bcb9-6ec8-4238-a2eb-9a3e58c3e387" />

Based on MATLAB scripts with the implementation of the LMS filter, coding is done in C language for the DSK613.

## Results
It is necessary to pause the program execution and then enter the address of the variable, which can be done directly with the address or with the name of the variable. After pressing enter, the contents of the memory in those variables are displayed. The format in which it is displayed is already in 64-bit floating point.

In MATLAB, the values obtained during execution are copied to the DSK6713 so that they can be graphed.
It is necessary to save the values of the memory space used by the variable y. Select the Save memory button.

The values are placed in the part of the MATLAB script that requires the variable y_asm to plot them. When the entire script is executed, the graph comparing the desired signal with the one calculated in MATLAB and the one calculated on the DSK6713 board is displayed.

It can be seen that the output signals in both implementations approximate the desired signal.

<img width="831" height="430" alt="image" src="https://github.com/user-attachments/assets/663c4272-112c-450b-b957-e0d93992bfd5" />
