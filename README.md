# IMPLEMENTATION-OF-CORDIC-ALGORITHM-USING-FPGA

### Abstract
An efficient way of obtaining  trigonometric, hyperbolic and logarithmic functions is provided by CORDIC algorithm. In this algorithm bit shifting operation replaces multiplication and iterative addition will result in accurate values of such trigonometric functions. Not only it is saving the area but also improves the throughput. Proposed CORDIC algorithm was simulated using Model sim software.


Keywords—CORDIC Algorithm, Linear iterations, Rotation mode, FPGA, Trigonometric functions, hyperbolic  functions,  VHDL

### INTRODUCTION 
CORDIC stands for COordinate Rotation DIgital Computer. In 1959, Jack E. Volder developed this algorithm which is used for solving the trigonometric relationships involved in plane coordinate rotation and conversion from rectangular to polar coordinates.

Robust technique, low-complexity and highly efficient CORDIC algorithm has attracted many real time applications, at initial days it was used in navigation problems. Later signal processing, adaptive filters, biomedical signal processing, neural networks, matrix-based computation (QR decomposition & SVD) started using it.

There exists three configuration to operate CORDIC algorithm.(i)linear (ii)circular (iii)Hyperbolic, and each of them functions either in vectoring mode or rotation mode. In rotation mode, the input vector is rotated by a specified angle, whereas in vectoring mode, the input vector is rotated to the x axis while recording the angle of rotation required.

CORDIC algorithm works in cycle using the shift and adds operations . Due to which this algorithm does not cover much space on the hardware,. Thus, it provides very quick operation 

The new vector v’ with coordinate (x’, y’) is obtained by rotating vector with coordinate (x, y) through an angle ∅i.  

From the basic rotation and transform equation.

            x'=x*cos∅-y*sin∅
            y'=y*cos∅+x*sin∅

The above equation can be rewritten as follows
            
            x'=cos∅(x-y*tan∅)
            y'=cos∅(y+x*tan∅)…..(1)

Here ∅ is angle of rotation and Ɵ is actual angle.
To simplify the above equations, we take  tan∅=2^(-i)  . This assumption make the ∅ to variate on the order of tan^(-1)⁡〖(2^(-i) 〗), the advantage is (1), (1/2),(1/4),..(1/8) can be performed just by right shifting in digital domain. Ki=cos∅ , is removed from the equation which will be multiplied at the later stage.
         
 ### DIGITAL IMPLEMENTATION-
 ![image](https://user-images.githubusercontent.com/85278130/121165020-9616d000-c86d-11eb-9838-a22a374e630b.png)

         FIG1:- Digital implementation of proposed algorithm
         
         
   ### INPUT 4 BIT INPUT VALUE AND CORRESPONDING OUTPUT ANGLE:

| 4 bit data    | Angle values  |
| ------------- | ------------- |
|     0000      |  0°/360°      |
|     0001      |   22.5°       |
|     0010      |   45°         |
|     0011      |   67.5°       |
|     0100      |   90°         |
|     0101      |   112.5°      |
|     0110      |   135°        |
|     0111      |   157.5°      |
|     1000      | 180°          |
|     1001      | 202.5°        |
|     1010      | 225°          |
|     1011      | 247.5°        |
|     1100      | 270°          |
|     1101      | 292.5°        |
|     1110      | 315°          |
|     1111      | 337.5°        |

The Algorithm is simulated in VIVADO 2019.1 and Model Sim Simulators.


### SIMULATION RESULTS

We will divide the Values of sin_op and cos_op by 10^5 as we took multiplier of 10^5 with input
so for example if input is 1111 so sin_op =-38270 so Our actual value of sing is -0.38270 Similarly for cos_op we will do the same

for 0 degree

![image](https://user-images.githubusercontent.com/85278130/121229356-72727a80-c8ab-11eb-8de5-4f13349f5d59.png)

     Fig2:- Simulation results for input z=0000 
for 112.5 degree

![image](https://user-images.githubusercontent.com/85278130/121229740-f9bfee00-c8ab-11eb-95d7-86524a2e3da3.png)
       
       Fig3:- Simulation results for input z=0101

for 225 degree        

![image](https://user-images.githubusercontent.com/85278130/121229922-325fc780-c8ac-11eb-85f6-cb61c2f44d6c.png)

     Fig4:- Simulation results for input z=1010

for 337.5 degree

![image](https://user-images.githubusercontent.com/85278130/121230139-7ce14400-c8ac-11eb-90e4-d384e7e6bf6c.png)

     Fig2:- Simulation results for input z=1111

### CONCLUSION
The angle coverage by CORDIC algorithm is [0° - 90° ], and cannot cover [0°- 360° ], which limits the calculation range of the algorithm. The angles which lies on second, third, fourth quadrant can be converted to first quadrant by flipping the angles. Then using the iterative CORDIC operations to evaluate sin, cos magnitude values. Further with the use of 2’s compliment the perfect sign is provided to the magnitude value of angle of respective quadrants. This design produces high throughput and less latency for continuous bits of input. The worst-case error of sin, cos values obtained from above implementation is 2.32×〖10〗^(-5) units.

### REFERENCES
[1]  M. Chinnathambi, N. Bharanidharan and S. Rajaram, "FPGA implementation of fast and area efficient CORDIC algorithm," 2014 International Conference on Communication and Network Technologies, Sivakasi, India, 2014, pp. 228-232, doi: 10.1109/CNT.2014.7062760.
[2]. M. Anas, R. S. Padiyar and A. S. Boban, "Implementation of cordic algorithm and design of high speed cordic algorithm," 2017 International Conference on Energy, Communication, Data Analytics and Soft Computing (ICECDS), Chennai, India, 2017, pp. 1278-1281, doi: 10.1109/ICECDS.2017.8389648
[3] Sahoo and M. Panigrahy, "Hardware Implementation of CORDIC Algorithm," 2018 International Conference on Applied Electromagnetics, Signal Processing and Communication (AESPC), Bhubaneswar, India, 2018, pp. 1-4, doi:10.1109/AESPC44649.2018.9033343.
