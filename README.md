# README lib60870-C                      {#mainpage}

lib60870 library for IEC 60870-5 based protocols in C
用于 IEC 60870-5 协议的 C 语言 lib60870 库

The current implementation contains code for the IEC 60870-5-101 (application layer and serial link layer) and IEC 60870-5-104 (protocool over TCP/IP) specifications.
当前实现包含针对 IEC 60870-5-101（应用层和串行链路层）和 IEC 60870-5-104（基于 TCP/IP 的协议）规范的代码。

Features:

support for all application layer message types
支持所有应用层消息类型
master and slave  主从
balanced and unbalanced link layers (for CS 101 serial communication)
平衡和不平衡链路层（用于 CS 101 串行通信）
client/server for CS 104 TCP/IP communication
客户端/服务器（用于 CS 104 TCP/IP 通信）
CS 104 redundancy group support
CS 104 冗余组支持
CS101 slave/CS104 server: file service support
CS101 从站/CS104 主站：文件服务支持
Supports most TLS features required by IEC 62351-3 (third party code mbedtls required)
支持 IEC 62351-3 所需的大部分 TLS 功能（需要第三方代码 mbedtls）
portable C99 code  可移植 C99 代码

Please also consider the User Guide and the API reference documentation (https://support.mz-automation.de/doc/lib60870/latest/)


## Compiling and running the examples: 编译和运行示例


In the lib60870-C folder build the library with 在 lib60870-C 文件夹中构建库

`make`

Go to the examples folder and build the examples with 前往示例文件夹并构建示例

`make`

in each examples' directory. 在每个示例目录中。

The library and examples can also be build with _CMake_. 库和示例也可以使用 CMake 构建。

To build the library in a separate folder create a new folder as subdirectory of
the project folder and run cmake to create the build files:
要在单独的文件夹中构建库，请创建项目文件夹的子文件夹，并运行 cmake 以创建构建文件：

`mkdir build`

`cd build`

`cmake ..`

## Building without common code and HAL 不使用通用代码和 HAL 构建

The library contains some common code and a platform abstraction layer (HAL) that is shared with
other protocol libraries of MZ Automation (e.g. libiec61850). In order to simplify using these
protocol libraries together it is possible to compile the library without the common parts.

This can be done by using the *WITHOUT_HAL* and *WITHOUT_COMMON* defines when calling make:

`make WITHOUT_HAL=1 WITHOUT_COMMON=1`

## Building with TLS support 带有 TLS 支持的构建

The library can be build with support for TLS. In order to do so you have to download mbedtls version 2.28.x.

Unpack the mbedtls tarball in the dependencies folder so that a folder

dependencies/mbedtls-2.28

exists.

The cmake build system will automatically detect the mbedtls source and build the library with TLS support and mbedtls included

When using make you have to call make with WITH_MBEDTLS=1

`make WITH_MBEDTLS=1`

## Library configuration 库配置

There are different runtime and compile-time configuration options.
有不同的运行时和编译时配置选项。

Compile time configuration options can be used to shrink down the library for small embedded systems. 
Compile time configuration can be changed by modifying the file _config/lib60870_config.h_.
编译时配置选项可用于缩减小型嵌入式系统中的库。编译时配置可以通过修改文件 config/lib60870_config.h 来更改。

## Memory allocation  内存分配

The library uses dynamic memory allocation (malloc/calloc wrapped by own functions that can be replaced when required).
该库使用动态内存分配（malloc/calloc 由自己的函数包装，可以在需要时替换）。

The CS104 slave uses dynamic memory allocation only at setup time (when calling the function _CS104_Slave_create_ and
_CS104_Slave_start_/_CS104_Slave_startThreadless_.
CS104 从设备仅在设置时间（调用 CS104_Slave_create 和 CS104_Slave_start/CS104_Slave_startThreadless 函数时）使用动态内存分配。

For details please have a look at the _User Guide_.

## Contact:

The library is developed by Michael Zillgith and supported by MZ Automation GmbH.

For bug reports, hints or support please contact info@mz-automation.de



## Licensing

This software can be dual licensed under the GPLv3 (https://www.gnu.org/licenses/gpl-3.0.en.html) and a commercial license agreement.

When using the library in commercial and non-GPL applications you should buy a commercial license.

## Commercial licenses and support

Support and commercial license options are provided by MZ Automation GmbH. Please contact info@mz-automation.de for more details.

## Contributing

If you want to contribute to the improvement and development of the library please send me comments, feature requests, bug reports, or patches.

For more than trivial contributions I require you to sign a Contributor License Agreement. Please contact info@libiec61850.ccom
