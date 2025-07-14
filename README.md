# robocupdemo_fix
这是中国地质大学（北京）地智行者队的代码

## 操作步骤及简要说明
 1.网线连接T1（ssh booster@192.168.10.102）
 2.sudo nmtui(连接场地WiFi）并ifconfig,查看IP地址
 3.使用远程sshh连接机器人（可以拔掉网线） ssh booster@IP地址

## 编译
./scripts/build.sh
## 运行
./scripts/start.sh

## 说明
1.在编译之前请检查brain.yaml中的机器人参数，如（方位left/right,角色striker/gokeeper）
2.请检查gamecontroller的配置文件中，裁判机的ip
3.检查机器人的teamID等相关信息

### 此仓库代码主要用于二次开发，修改之后需虚拟仿真之后，再前往真机部署测试，目前已修改vxfactor(0.90 ->1.00)

# 重定位修改
## 集成 IMU 数据：
在 calcProbs 方法开始处，通过 brain->data->robotPoseToField.theta 获取当前机器人的 IMU 方向。
计算方向权重：
针对每个粒子，通过计算粒子的角度与 IMU 方向的差异（利用 toPInPI 标准化角度差），使用高斯函数（σ=0.1）计算方向权重。
调整概率计算：
将方向权重乘入基于残差计算出的概率，提升方向估计的鲁棒性与精度。
最终结果：
在不改变方法签名的前提下，实现了对 IMU 数据的融合，从而提高定位算法的精度。

