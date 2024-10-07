# Ground-effect-controller

Ground-Effect-Aware Modeling and Control for Multicopters.



<p align="center">
    <img src="./figs/header.jpg" alt="Alt text" style="zoom:30%;" />
</p>


## The quadrotor

### Firmware for the flight controller 

This firmware is included in a [VMware](https://www.vmware.com/) virtual machine environment.

Downlink:  [Fireware with virtual environment](http://zjufast.tpddns.cn:9110/share.cgi?ssid=cfde8ecbb0b8432fb59c241b98ab59a9)

Downlink:  [Fireware only](http://zjufast.tpddns.cn:9110/share.cgi?ssid=d6dd0e1a97cf43f7a9f5feb82fca04d5)

Password: fastlab@2024

### CAD model

The CAD model of  the [quadrotor](./CAD/quadrotor.STEP)  in this paper.



<img src="./figs/quadrotor.PNG" alt="Alt text" style="zoom:35%;" />

### BOM list

| **Type**                         | **Name**                                   | **Mass (g)** | **Quantity** | **Gross Mass (g)** |
| -------------------------------- | ------------------------------------------ | ------------ | ------------ | ------------------ |
| **Rack**                         | Upper center plate                         | 112.80       | 1            | 112.80             |
|                                  | Lower center plate                         | 150.00       | 1            | 150.00             |
|                                  | Flight controller base PCB                 | 14.00        | 1            | 14.00              |
|                                  | Flight controller core PCB                 | 10.50        | 1            | 10.50              |
|                                  | Flight controller                          | 41.30        | 1            | 41.30              |
| **Rack mounting**                | M3 Lockout nuts                            | 0.40         | 20           | 8.00               |
|                                  | M3 Isolation column (6mm)                  | 0.18         | 20           | 3.56               |
|                                  | M3 screw (16mm)                            | 1.04         | 20           | 20.80              |
| **Undercarriage**                | Landing gear carbon clamp                  | 4.90         | 4            | 19.60              |
|                                  | Landing gear carbon tube spacer            | 4.23         | 4            | 16.93              |
|                                  | Landing gear carbon tube                   | 2.50         | 4            | 10.00              |
|                                  | Landing gear carbon tube sponge cylinder   | 3.25         | 4            | 13.00              |
|                                  | Landing gear carbon tube sponge round pad  | 0.40         | 4            | 1.59               |
|                                  | Motor                                      | 45.00        | 4            | 180.00             |
|                                  | Paddle (7 inches)                          | 7.50         | 4            | 30.00              |
|                                  | M3 screw (20mm)                            | 1.23         | 16           | 19.68              |
| **Onboard computer and battery** | 3D printed parts (on-board computer fixed) | 56.50        | 1            | 56.50              |
|                                  | Intel NUC                                  | 494.20       | 1            | 494.20             |
|                                  | SSD                                        | 8.80         | 1            | 8.80               |
|                                  | RAM                                        | 8.20         | 2            | 16.40              |
|                                  | Battery 22.2V 1400mAh                      | 233.80       | 1            | 233.80             |
|                                  | Reflector bracket                          | 31.50        | 1            | 31.50              |
|                                  | Reflective (25mm)                          | 6.52         | 5            | 32.60              |
| **Laser sensor and fixation**    | M3 screw (10mm)                            | 0.77         | 8            | 6.16               |
|                                  | M3 Lockout nuts                            | 0.40         | 8            | 3.20               |
|                                  | M3 screw (16mm)                            | 1.04         | 4            | 4.16               |
|                                  | M3 Isolation column (6mm)                  | 0.18         | 4            | 0.71               |
|                                  | M3 single pass aluminum column (12mm)      | 0.60         | 4            | 2.40               |
|                                  | M3 Lockout nuts                            | 0.40         | 4            | 1.60               |
|                                  | Laser sensors fix carbon plates            | 10.60        | 1            | 10.60              |
|                                  | Laser sensor                               | 8.30         | 1            | 8.30               |
| **Total**                        |                                            |              |              | **1562.70**        |

## The force measurement platform

### CAD model

The  [CAD model](./CAD/platform.step)  of the force measurement platform in this paper.

<img src="./figs/platform.PNG" alt="Alt text" style="zoom:30%;" />

### Platform data

For example, the following [figure](./figs/getorque_all_rpmmodel.pdf) shows the data in the leveling torque experiment. The figure shows the relationship between leveling torque **${{\bf{\tau }}_G}$** and average rotor speed **$\left\| {{n_i}} \right\|$**. The black points are sensor data and the blue lines are model-fitting results.



<img src="./figs/getorque_all_rpmmodel.jpg" alt="Alt text" style="zoom:35%;" />

## Motor calibration and rotor speed control

### Motor model

To control the rotors to the desired speeds, the rotors need to be modeled and calibrated.

The thrust **$T_i$** and torque **$M_i$** generated by a single rotor are:

\[
T_i = k_T n_i^2 \\
M_i = k_I n_i^2 + J_R \dot{n_i},
\]

where:
- **$k_T$** is the thrust coefficient,
- **$k_I$** is the torque coefficient,
- **$J_R$** is the moment of inertia of the rotor,
- and **$i$** is the rotor number.



<img src="./figs/sigle_motor_platform.jpg" alt="Alt text" style="zoom:30%;" />



### Throttol model of the flight controller



<img src="./figs/id_single_motor.jpg" alt="Alt text" style="zoom:30%;" />



### Rotor speed control







## Parameters in the paper

The results of parameter identification in the paper are shown in following table:

| **Symbol**   | **Value**                                                    | **Name**                             | **Method**              |
| ------------ | ------------------------------------------------------------ | ------------------------------------ | ----------------------- |
| **$k_T$**    | $4.0083 \times 10^{-8} \, \text{N/rpm}^2$                    | Thrust coefficient                   | Single-rotor platform   |
|              | $3.7840 \times 10^{-8} \, \text{N/rpm}^2$                    |                                      | Quadrotor platform      |
|              | $4.2958 \times 10^{-8} \, \text{N/rpm}^2$                    |                                      | Real flight by hovering |
| **$k_{TX}$** | $4.678 \times 10^{-8} \, \text{N/rpm}^2$                     | Torque by thrust coefficient (roll)  | Quadrotor platform      |
| **$k_{TY}$** | $3.588 \times 10^{-8} \, \text{N/rpm}^2$                     | Torque by thrust coefficient (pitch) |                         |
| **$k_I$**    | $6.3859 \times 10^{-10} \, \left( \text{N} \cdot \text{m} \right) / \text{rpm}^2$ | Rotor torque coefficient             | Single-rotor platform   |
| **$J_R$**    | $1.0556 \times 10^{-4} \, \text{kg/m}^2$                     | Rotor inertia                        | Single-rotor platform   |
| **$g_1$**    | $1.804 \times 10^{-2}$                                       | Ground effect coefficient            | Quadrotor platform      |
| **$g_2$**    | $7.339 \times 10^{-3}$                                       |                                      |                         |
| **$g_3$**    | $-3.365 \times 10^{-1}$                                      |                                      |                         |
| **$g_4$**    | $4.126 \times 10^{-2}$                                       |                                      |                         |
| **$g_5$**    | $6.494 \times 10^{-2}$                                       |                                      |                         |
| **$c_2$**    | $-1.448471 \times 10^8$                                      | Throttle curve parameter             | Quadrotor platform      |
| **$c_1$**    | $5.228928 \times 10^8$                                       |                                      |                         |
| **$c_0$**    | $1.033111 \times 10^8$                                       |                                      |                         |
| **$d_x$**    | $0.3970 \, \text{N/(m/s)}$                                   | Rotor drag coefficient               | Real flight             |
| **$d_y$**    | $0.3300 \, \text{N/(m/s)}$                                   |                                      |                         |
| **$m$**      | $1.696 \, \text{kg}$                                         | Mass of the quadrotor                | Electronic scale        |
|              | $1.562 \, \text{kg}$                                         |                                      | Mechanical model        |
| **$I_x$**    | $0.00745220 \, \text{kg/m}^2$                                | Inertia of the quadrotor             | Mechanical model        |
| **$I_y$**    | $0.00792752 \, \text{kg/m}^2$                                |                                      |                         |
| **$I_z$**    | $0.01249522 \, \text{kg/m}^2$                                |                                      |                         |

## Control algorithm

The  following [figure](./figs/traj_rmse_plot.pdf) shows the curves of Exp.~7($3m/s$, near-ground) in the paper. Every loop is well-controlled, including the rotor speed, thrust acceleration, body torque, etc.

The control algorithm that runs on the onboard computer will be uploaded soon.



<p align="center">
    <img src="./figs/traj.gif" alt="Alt text" style="zoom:80%;" />
</p>



<img src="./figs/traj_rmse_plot.jpg" alt="Alt text" style="zoom:40%;" />



