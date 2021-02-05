#### Comm.h

**Cartesian** (float x, float y, float z)
卡迪尔坐标系

**IMU** (float quaternion[4], float gyroscope陀螺仪[3],float accelerometer[3], float rpy[3], int8 temerature )
包括陀螺仪、加速度计、温度，解算出的欧拉角与四元数

**LED** (uint8 r , uint8 g, uint8 b)

**MotorState** (unit8 mode电机工作模式, float q当前角度, float dq当前速度, float ddq当前加速度, float tauEst,  float q_raw, float dq_raw, float dqq_raw. int8 temperature, unit32 reserve[2])
包括目标电机双编码器的位置、速度、转矩、温度，以及工作模式； 电机反馈数据

**MotorCmd**  (unit8 mode 期望的电机工作模式, float q期望的角度, float dq, float tau, float Kp, float Kd, unit32 reserve[3])

MoterCmd.mode： 0x00 电子刹车制动 0x0A 伺服
包括目标电机的位置、速度、转矩、刚度系数、阻尼系数，以及工作模式； 电机指令

**LowState** (unit8 levelFlag , uint16 commVersion, unit16 robotID, uint32 SN, unit8 bandWidth, IMU imu, MotorState moterState[20] 20个电机状态, int16 footForce[4], int16 footForceEst[4], uint32 tick, unit8 uirelessRemote[40], uint32 reserve, uint32 crc)
底层控制模式反馈

**LowCmd** (unit8 levelFlag , uint16 commVersion, unit16 robotID, uint32 SN, unit8 bandWidth, MotorCmd moterCmd[20] 20个电机状态, LED led[4], unit8 uirelessRemote[40], uint32 reserve, uint32 crc)
底层控制指令

#### 安全 safety.h

**PositionLimit** 只在position mode的底层控制下生效
**PowerProtect** 只在底层控制下生效
**PositionProtect** 切换关节纯阻尼状态