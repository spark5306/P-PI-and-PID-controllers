
# Analysis of P, PI and PID Controllers using MATLAB
## Aim:
To analyse the effect of P, PI and PID controllers for the system having open loop transfer function, G(S)=1/(S^2+10S+20) using MATLAB. 
## Apparatus Required:
Computer with MATLAB software

## Theory:
	A controller is a device introduced in the system to modify the error signal and to produce a control signal. 
	The way the controller produces the control signal is called the control action.

Consider the following unity feedback system,
 <img width="823" height="281" alt="image" src="https://github.com/user-attachments/assets/36e49512-cf47-4fec-b00c-f79dc0af1c5f" />

### Proportional (P) Controller:
The proportional controller produces an output, which is proportional to error signal.<br>
u(t)∝e(t) <br>
⇒u(t)=Kpe(t) <br>
Apply Laplace transform on both the sides - <br>
U(s)=KpE(s) <br>
U(s)/E(s)=Kp <br>
Therefore, the transfer function of the proportional controller is Kp.

### Proportional Integral (PI) Controller:
The proportional integral controller produces an output, which is the combination of outputs of the proportional and integral controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s)E(s) <br>
U(s)/E(s)=Kp+Ki/s <br>
Therefore, the transfer function of proportional integral controller is Kp+Kis. <br>

### Proportional Integral Derivative (PID) Controller:
The proportional integral derivative controller produces an output, which is the combination of the outputs of proportional, integral and derivative controllers. <br>
u(t)=Kp e(t)+Ki ∫e(t)dt+ Kd (de(t)/dt) <br>
Apply Laplace transform on both sides - <br>
U(s)=(Kp+Ki/s+Kds)E(s) <br>
U(s)/E(s)=Kp+Ki/s+Kd s <br>
Therefore, the transfer function of the proportional integral derivative controller is Kp+Ki/s+Kd s

### Characteristics of Kp, Ki and Kd terms:

Increasing the proportional gain ( ) has the effect of proportionally increasing the control signal for the same level of error. The fact that the controller will "push" harder for a given level of error tends to cause the closed-loop system to react more quickly, but also to overshoot more. Another effect of increasing   is that it tends to reduce, but not eliminate, the steady-state error.
The addition of a derivative term to the controller ( ) adds the ability of the controller to "anticipate" error. With derivative control, the control signal can become large if the error begins sloping upward, even while the magnitude of the error is still relatively small. This anticipation tends to add damping to the system, thereby decreasing overshoot. The addition of a derivative term, however, has no effect on the steady-state error.
The addition of an integral term to the controller ( ) tends to help reduce steady-state error. If there is a persistent, steady error, the integrator builds and builds, thereby increasing the control signal and driving the error down. 
 


## Procedure:
	Open MATLAB software
	Open a new script file.
	Type the program.
	Save and Execute the program.
	Determine the steady state error and analyse the controllers.
## Program: 
### Without Controller (Open loop System)
```
num=[1];
den=[1 10 20];
sys=tf(num,den)
step(sys)
```
### With P-Controller
```
num=[1];
den=[1 10 20];
sys=tf(num,den)
Kp=300;
C=pid(Kp);
T=feedback(C*sys,1);
step(T)
```
### With PI Controller
```
num=[1];
den=[1 10 20];
sys=tf(num,den)
Kp=30;
Ki=70;
C=pid(Kp,Ki);
T=feedback(C*sys,1);
step(T)
```
### With PID Controller
```
num=[1];
den=[1 10 20];
sys=tf(num,den)
Kp=350;
Ki=300;
Kd=50;
C=pid(Kp,Ki,Kd);
T=feedback(C*sys,1);
step(T)
```
## Output: 
### Without Controller (Open loop System)
<img width="696" height="616" alt="Screenshot 2025-10-24 085159" src="https://github.com/user-attachments/assets/aeed3ecf-db38-46c9-b6ad-6881fba42b37" />


### With P-Controller
<img width="697" height="627" alt="Screenshot 2025-10-24 085429" src="https://github.com/user-attachments/assets/f3fffa3b-abfb-47ac-9894-158c91eb97d5" />



### With PI Controller
<img width="698" height="619" alt="Screenshot 2025-10-24 085640" src="https://github.com/user-attachments/assets/9161a7f8-2278-44bb-b249-908b13eb1eec" />


### With PID Controller
<img width="694" height="620" alt="Screenshot 2025-10-24 085814" src="https://github.com/user-attachments/assets/5b202b33-4b14-4963-8e25-3cae02e0f89f" />



## Result:
Thus the P, PI and PID controllers for the given system was analysed and the following conclusions were arrived using MATLAB. <br>
### With-out controller 
Delay time =  0.4s        
Rise time =   1.1s         
Peak time =    ∞/UNDEFINED      
Settling time =  2.6s          
Steady State Error = 0.95       
### With P Controller
Delay time = 0.06 s
Rise time =  0.01 s        
Peak time =   0.13 s        
Settling time =  0.17 s          
Steady State Error =  0.06      
### With PI Controller 
Delay time =  0.3 s       
Rise time =   0.5 s          
Peak time =   0.95  s      
Settling time = 1.3  s         
Steady State Error =  0      
### With PID Controller 
Delay time =  0.04 s       
Rise time =   0.09 s          
Peak time =   0.25 s        
Settling time =  0.5 s        
Steady State Error =  0      
