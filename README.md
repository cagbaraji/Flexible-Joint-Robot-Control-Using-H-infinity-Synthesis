# Flexible-Joint-Robot-Control-Using-H-infinity-Synthesis

## Introduction
There has been a rapid increase in the application of flexible joint robots in modern automation and robotics due to their energy efficiency, light-weight structure and cost-effectiveness. The flexible joint robot, unlike the rigid robots, incorporates elasticity features directly in the joints, resulting to increase in complexity of the dynamic behaviors. Despite the advantages of the flexibility property of the flexible joint robots for safety and energy absorption, it introduces vibrational modes and resonance, causing degradation in control performance and this can lead to some challenges such as instability.

To address this issue, the flexible joint robot requires a controller and this process presents unique and vital challenges, especially when high accuracy and robustness against external disturbances, model uncertainties and unmodeled dynamics are required. The traditional control techniques lack the ability to address these challenges, particularly when high-frequency dynamics becomes important or when system parameters vary significantly.

This study focuses on the design of a robust controller for a flexible joint robot using H-infinity control synthesis which was compared with PID control method. The H-infinity controller design method is well-suited for high-order systems and systems with uncertainties, delivering high precision and stability margins by reducing the worst-case gain from disturbances to the output performance. The robust controller design considers a linearized dynamic model of the robot as the base, including real-world parameters as gravitational force, damping, and joint elasticity. 

The objectives of this research are to design and evaluate a robust controller for the flexible joint robot that can achieve and maintain optimal trajectory tracking and disturbance rejection under significant model uncertainties. The output of the controlled system performance is analyzed both in time-domain and frequency-domain and the resulting robust controller is implemented and tested using MATLAB and Simulink tools. 

## Methodology
### Flexible Joint Robot Model

Considering the robotic link or arm rotating on a horizontal plane and actuated with a motor through elastic joint coupling (Farid and Benjamin, 2009). Let q_a be the link angular displacement (i.e the link output to be analyzed and controlled) and q_m be the motor angular position. Then, typical flexible joint robotic arm dynamic model can be described by the dynamic equations as presented in (Adel and Jason, 2009; An-Chyau and Yuan-Chih, 2004) as follows:

![image](https://github.com/user-attachments/assets/362d526a-6ab7-48d0-9803-eb14ba97e406)

![image](https://github.com/user-attachments/assets/cf82d091-56ef-4127-9be4-db5a625961c8)

The transfer function, in s-domain, of the system is given by (Adel and Jason, 2009; An-Chyau and Yuan-Chih, 2004) as follows:

![image](https://github.com/user-attachments/assets/71e8ff5d-387b-4889-b7b6-e97af1a3259e)

### PID Control Method

The PID control method was applied on the FJR to improve the performance of the FJR based on the reduction it’s settling time, the tracking error and improve its stability margins. PID control method used the three terms, Proportional-Integral-Derivative control functions to compensate or control the error generated from the difference between the actual output and the desired output or reference input. The ability of the controller to reduce this error to zero becomes the major objective of this method. Figure 1 shows the PID control of the Flexible joint robot block diagram.

![image](https://github.com/user-attachments/assets/b21468cb-b042-44ce-bf32-e1904aea52c5)

Figure 1: Controlled Flexible joint robot block diagram

Applying PID controller design method, we have
![image](https://github.com/user-attachments/assets/7e80f2a5-85e3-4a99-b617-c9520c8b1492)

### H-Infinity Control Method
Applying H-infinity controller design method, we hve:

![image](https://github.com/user-attachments/assets/912cbbaf-fac0-4c86-ab35-e6cfad6c2ea1)

Figure 2: Controlled flexible joint robot using H-infinity

### The H-infinity control design algorithm

i.	Apply flexible joint transfer function G,

![image](https://github.com/user-attachments/assets/ffec2f99-1b69-4587-aea0-7e07c0881b6b)

ii. Apply the weighting functions W1(s) and W2(s) on the flexible joint transfer function G(s) Form the augmented function P(s) with G(s), W1(s) and W2(s) using MATLAB operator, aug:
    P(s)=aug(G,W1,W2) 	

iii. 	Generate the controller K in state space using the mixsyn syntax in MATLAB that can improve the output of the system and satisfy the desired characteristics:
    [K]=hinfsyn(P) 

iv. 	Compute the open loop gain function:
    L=K×G 

v. vi.	Compute the improved flexible joint function T(s):

![image](https://github.com/user-attachments/assets/e9548d74-3f34-4b94-98d6-6200870eaa41)

vi. Plot a time domain graph for the existing flexible joint model function G(s) to determine the damping time.
	
vii. Plot a frequency domain graph for the existing flexible joint model function G(s) to determine the tracking error and the stability of the existing joint model.

viii. Plot a time domain graph for the improved flexible joint model function T(s) to determine damping time.

ix. Plot a frequency domain graph for the improved flexible joint model function T(s) to determine the tracking error.

x. Plot a frequency domain graph for the open loop function L(s) to determine the stability of the improved flexible joint model.

## Results

![image](https://github.com/user-attachments/assets/d628c943-d83c-4d6b-8d6d-93f681670bcc)

Figure 3: Step response of the PID controlled FJR

![image](https://github.com/user-attachments/assets/4730ed75-d36c-4a9b-8acb-239e406d0856)

Figure 4:  Bode plot of the PID control

![image](https://github.com/user-attachments/assets/e2e83771-3fe0-4c7e-9dae-4eab19ca5b70)

Figure 5: Step function response of the H-infinity control

![image](https://github.com/user-attachments/assets/b781ff36-dfdf-4089-be89-b3659a2d2d3f)

Figure 6: Bode plot of the H-infinity control

The designed robust controller using H-infinity can be expressed in state space fomate as follows:

![image](https://github.com/user-attachments/assets/6354b683-06c7-44e5-8c3f-750360bb93fe)
