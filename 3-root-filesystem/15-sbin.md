# /sbin：系统二进制文件

### 3.15.1. 用途

系统管理员使用的工具（和其他只有root使用的命令）保存在`/sbin`、`/usr/sbin`和`/usr/local/sbi`n中。`/sbin`包含除了`/bin`中之外其他的启动、还原、恢复和/或修复系统所必需的二进制文件[^18]。

在已知`/usr`已经挂载（并且没有问题）的情况下执行的程序通常位于`/usr/sbin`下。本地安装的系统管理程序应该位于`/usr/local/sbin`下[^19]。


### 3.15.2. 要求
`/sbin`下应该有以下命令或符号链接。

命令	|描述
--------|------------------
shutdown	|关闭系统的命令

### 3.15.3. 特殊选项

如果安装了相应子系统，`/sbin`下必须有以下文件或符号链接：

命令	|描述
--------|-------------------------------------------------
fastboot	|不检查磁盘重启系统（可选）
fasthalt	|不检查磁盘停止系统（可选）
fdisk	|操作分区表（可选）
fsck	|文件系统检查和修复工具（可选）
fsck.*	|针对某一特定文件系统的检查和修复工具（可选）
getty	|`getty`程序（可选）
halt	|停止系统的命令（可选）
ifconfig	|配置网络接口的命令（可选）
init	|初始化进程（可选）
mkfs	|创建文件系统的命令（可选）
mkfs.*	|创建特定文件系统的命令（可选）
mkswap	|设置交换区的命令（可选）
reboot	|重启系统的命令（可选）
route	|IP路由表工具（可选）
swapon	|启用分页和交换（可选）
swapoff	|关闭分页和交换（可选）
update	|周期性的清洗文件系统缓存区的后台服务（可选）

---
[^18]: 原来，/sbin二进制文件保存在/etc下。
[^19]: 决定哪些东西应该放在“`sbin`”中很简单：如果一个正常（非系统管理员）用户有时会直接运行它，那它必须放在某一“`bin`”文件夹中。普通用户的路径中应该不必出现`sbin`文件夹。</br>例如，像chfn这样用户只是使用的文件仍然必须放在`/usr/bin`中。`ping`这个命令尽管对于`root`是绝对必须的（网络还原和诊断），却经常被用户使用，所以必须驻留在`/bin`下。</br>我们推荐用户对于`/sbin`下的所有东西有读和执行的权限，除了一些可能进行了`setuid`和`setgid`设置的程序。区分`/bin`和`/sbin`不是为了安全原因或阻止用户查看操作系统，而是为了清晰地区别每个人都能用的和最初用于系统管理任务的二进制文件。把用户拦在`/sbin`外也起不到实质的提升安全性的作用。
