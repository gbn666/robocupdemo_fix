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

