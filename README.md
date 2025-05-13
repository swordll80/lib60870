# README lib60870-C                      {#mainpage}

lib60870 library for IEC 60870-5 based protocols in C
���� IEC 60870-5 Э��� C ���� lib60870 ��

The current implementation contains code for the IEC 60870-5-101 (application layer and serial link layer) and IEC 60870-5-104 (protocool over TCP/IP) specifications.
��ǰʵ�ְ������ IEC 60870-5-101��Ӧ�ò�ʹ�����·�㣩�� IEC 60870-5-104������ TCP/IP ��Э�飩�淶�Ĵ��롣

Features:

support for all application layer message types
֧������Ӧ�ò���Ϣ����
master and slave  ����
balanced and unbalanced link layers (for CS 101 serial communication)
ƽ��Ͳ�ƽ����·�㣨���� CS 101 ����ͨ�ţ�
client/server for CS 104 TCP/IP communication
�ͻ���/������������ CS 104 TCP/IP ͨ�ţ�
CS 104 redundancy group support
CS 104 ������֧��
CS101 slave/CS104 server: file service support
CS101 ��վ/CS104 ��վ���ļ�����֧��
Supports most TLS features required by IEC 62351-3 (third party code mbedtls required)
֧�� IEC 62351-3 ����Ĵ󲿷� TLS ���ܣ���Ҫ���������� mbedtls��
portable C99 code  ����ֲ C99 ����

Please also consider the User Guide and the API reference documentation (https://support.mz-automation.de/doc/lib60870/latest/)


## Compiling and running the examples: ���������ʾ��


In the lib60870-C folder build the library with �� lib60870-C �ļ����й�����

`make`

Go to the examples folder and build the examples with ǰ��ʾ���ļ��в�����ʾ��

`make`

in each examples' directory. ��ÿ��ʾ��Ŀ¼�С�

The library and examples can also be build with _CMake_. ���ʾ��Ҳ����ʹ�� CMake ������

To build the library in a separate folder create a new folder as subdirectory of
the project folder and run cmake to create the build files:
Ҫ�ڵ������ļ����й����⣬�봴����Ŀ�ļ��е����ļ��У������� cmake �Դ��������ļ���

`mkdir build`

`cd build`

`cmake ..`

## Building without common code and HAL ��ʹ��ͨ�ô���� HAL ����

The library contains some common code and a platform abstraction layer (HAL) that is shared with
other protocol libraries of MZ Automation (e.g. libiec61850). In order to simplify using these
protocol libraries together it is possible to compile the library without the common parts.

This can be done by using the *WITHOUT_HAL* and *WITHOUT_COMMON* defines when calling make:

`make WITHOUT_HAL=1 WITHOUT_COMMON=1`

## Building with TLS support ���� TLS ֧�ֵĹ���

The library can be build with support for TLS. In order to do so you have to download mbedtls version 2.28.x.

Unpack the mbedtls tarball in the dependencies folder so that a folder

dependencies/mbedtls-2.28

exists.

The cmake build system will automatically detect the mbedtls source and build the library with TLS support and mbedtls included

When using make you have to call make with WITH_MBEDTLS=1

`make WITH_MBEDTLS=1`

## Library configuration ������

There are different runtime and compile-time configuration options.
�в�ͬ������ʱ�ͱ���ʱ����ѡ�

Compile time configuration options can be used to shrink down the library for small embedded systems. 
Compile time configuration can be changed by modifying the file _config/lib60870_config.h_.
����ʱ����ѡ�����������С��Ƕ��ʽϵͳ�еĿ⡣����ʱ���ÿ���ͨ���޸��ļ� config/lib60870_config.h �����ġ�

## Memory allocation  �ڴ����

The library uses dynamic memory allocation (malloc/calloc wrapped by own functions that can be replaced when required).
�ÿ�ʹ�ö�̬�ڴ���䣨malloc/calloc ���Լ��ĺ�����װ����������Ҫʱ�滻����

The CS104 slave uses dynamic memory allocation only at setup time (when calling the function _CS104_Slave_create_ and
_CS104_Slave_start_/_CS104_Slave_startThreadless_.
CS104 ���豸��������ʱ�䣨���� CS104_Slave_create �� CS104_Slave_start/CS104_Slave_startThreadless ����ʱ��ʹ�ö�̬�ڴ���䡣

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
