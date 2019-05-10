---
title: 用于按配置文件优化的环境变量
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195257"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>用于按配置文件优化的环境变量

有三个影响与创建的映像上的测试方案的环境变量 **/ltcg: pgi**用于按配置文件优化的：

- **PogoSafeMode**指定是否为应用程序分析使用快速模式或安全模式。

- **VCPROFILE_ALLOC_SCALE**中添加其他内存以供探查器。

- **VCPROFILE_PATH** ，可以指定用于.pgc 文件的文件夹。

**PogoSafeMode 和 VCPROFILE_ALLOC_SCALE 环境变量，从 Visual Studio 2015 开始已弃用。** 链接器选项[/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)并[/USEPROFILE](reference/useprofile.md)为这些环境变量指定相同的链接器行为。

## <a name="pogosafemode"></a>PogoSafeMode

此环境变量已被弃用。 使用**EXACT**或**NOEXACT**自变量 **/GENPROFILE**或者 **/FASTGENPROFILE**以控制此行为。

清除或设置**PogoSafeMode**环境变量以指定是否为应用程序分析在 x86 上使用快速模式或安全模式的系统。

按配置优化 (PGO) 在分析阶段有两个可能的模式：*快速模式*并*安全模式下*。 分析在快速模式下时，它使用**INC**指令来增加数据计数器。 **INC**指令速度更快，但不是线程安全的。 分析在安全模式下时，它使用**LOCK INC**指令来增加数据计数器。 **LOCK INC**指令具有相同的功能**INC**指令，并且是线程安全的但它是比慢**INC**指令。

默认情况下，PGO 分析以快速模式操作。 **PogoSafeMode**是仅在需要你想要使用安全模式。

若要运行 PGO 分析在安全模式下，必须使用环境变量**PogoSafeMode**或链接器开关 **/PogoSafeMode**，取决于系统。 如果您正在执行分析在 x64 计算机，必须使用链接器开关。 如果您正在执行在 x86 上进行分析计算机，你可以使用链接器设置或切换**PogoSafeMode**开始优化过程之前的任何值的环境变量。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 语法

> **set PogoSafeMode**[**=**_value_]

设置**PogoSafeMode**为任何值，以启用安全模式。 没有要清除以前的值并重新启用快速模式的值设置。

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

此环境变量已被弃用。 使用**MEMMIN**并**MEMMAX**自变量 **/GENPROFILE**或者 **/FASTGENPROFILE**以控制此行为。

修改**VCPROFILE_ALLOC_SCALE**环境变量，若要更改的内存量分配为保存的配置文件数据。 在极少数情况下，将不会有足够的内存可用于支持运行测试方案时收集配置文件数据。 在这些情况下，您可以通过设置增加的内存量**VCPROFILE_ALLOC_SCALE**。 如果在测试运行期间，该值指示具有足够的内存中收到一条错误消息，将分配到更大的值**VCPROFILE_ALLOC_SCALE**，直到在测试运行完成，但没有内存不足错误。

### <a name="vcprofileallocscale-syntax"></a>VCPROFILE_ALLOC_SCALE 语法

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value*参数是用于运行测试方案所需的内存量的缩放系数。  默认值为 1。 例如，此命令行设置的缩放比例为 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

使用**VCPROFILE_PATH**环境变量以指定要创建的.pgc 文件的目录。 默认情况下，在所分析的二进制文件所在的同一目录中创建.pgc 文件。 但是，如果二进制文件的绝对路径不存在，因为其中生成二进制文件的不同计算机上运行配置文件方案的情况下可能会出现这种情况，则可以设置**VCPROFILE_PATH**为目标计算机存在的路径。

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH 语法

> **set VCPROFILE_PATH**[**=**_path_]

设置*路径*到要在其中添加的.pgc 文件的目录路径的参数。 例如，此命令行到 C:\profile 设置的文件夹：

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>请参阅

[按配置文件优化](profile-guided-optimizations.md)<br/>
[/GENPROFILE 和 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
