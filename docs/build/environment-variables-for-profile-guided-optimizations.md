---
title: 用于按配置优化的环境变量
ms.date: 03/14/2018
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
ms.openlocfilehash: 099e57f1ac69223adafe7bec1af4cc3452915e86
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195257"
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>用于按配置优化的环境变量

有三个环境变量可影响使用 /LTCG:PGI  创建的映像上的测试方案，以便按配置优化：

- PogoSafeMode  指定对应用程序分析是使用快速模式还是安全模式。

- VCPROFILE_ALLOC_SCALE  添加额外内存供探查器使用。

- VCPROFILE_PATH  使你可以指定用于 .pgc 文件的文件夹。

从 Visual Studio 2015 开始，PogoSafeMode 和 VCPROFILE_ALLOC_SCALE 环境变量已弃用。  链接器选项 [/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md) 和 [/USEPROFILE](reference/useprofile.md) 指定与这些环境变量相同的链接器行为。

## <a name="pogosafemode"></a>PogoSafeMode

此环境变量已弃用。 对 /GENPROFILE 或 /FASTGENPROFILE 使用 EXACT 或 NOEXACT 参数可控制此行为     。

清除或设置 PogoSafeMode  环境变量可指定在 x86 系统上对应用程序分析是使用快速模式还是安全模式。

按配置优化 (PGO) 在分析阶段有两种可能的模式：快速模式  和安全模式  。 当分析处于快速模式时，它使用 INC  指令增加数据计数器。 INC  指令速度更快，但不是线程安全的。 当分析处于安全模式时，它使用 LOCK INC  指令增加数据计数器。 LOCK INC  指令的功能与 INC  指令相同，并且是线程安全的，但它比 INC  指令更慢。

默认情况下，PGO 分析在快速模式下运行。 仅当要使用安全模式时，才需要 PogoSafeMode  。

若要在安全模式下运行 PGO 分析，必须使用环境变量 PogoSafeMode  或链接器开关 /PogoSafeMode  ，具体取决于系统。 如果要在 x64 计算机上执行分析，则必须使用链接器开关。 如果要在 x86 计算机上执行分析，则可以使用链接器开关，或在开始优化过程之前将 PogoSafeMode  环境变量设置为任意值。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 语法

> set PogoSafeMode  [=  value  ]

将 PogoSafeMode  设置为任意值都可启用安全模式。 在没有值的情况下设置可清除以前的值并重新启用快速模式。

## <a name="vcprofile_alloc_scale"></a>VCPROFILE_ALLOC_SCALE

此环境变量已弃用。 对 /GENPROFILE 或 /FASTGENPROFILE 使用 MEMMIN 或 MEMMAX 参数可控制此行为     。

修改 VCPROFILE_ALLOC_SCALE  环境变量可更改分配用于保存配置文件数据的内存量。 在极少数情况下，在运行测试方案时，可用内存不足，无法支持收集配置文件数据。 在这些情况下，可以通过设置 VCPROFILE_ALLOC_SCALE  来增加内存量。 如果在测试运行期间收到指示内存不足的错误消息，请将更大的值分配给 VCPROFILE_ALLOC_SCALE  ，直到测试在没有内存不足错误的情况下运行完成。

### <a name="vcprofile_alloc_scale-syntax"></a>VCPROFILE_ALLOC_SCALE 语法

> set VCPROFILE_ALLOC_SCALE  [=  scale_value  ]

scale_value  参数是运行测试方案所需的内存量的比例因子。  默认值为 1。 例如，以下命令行将比例因子设置为 2：

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofile_path"></a>VCPROFILE_PATH

使用 VCPROFILE_PATH  环境变量可指定用于创建 .pgc 文件的目录。 默认情况下，将在要分析的二进制文件所在的目录中创建 .pgc 文件。 但是，如果该二进制文件的绝对路径不存在（在与生成二进制文件的计算机不同的计算机上运行配置文件方案时可能会出现这种情况），则可以将 VCPROFILE_PATH  设置为目标计算机上存在的路径。

### <a name="vcprofile_path-syntax"></a>VCPROFILE_PATH 语法

> set VCPROFILE_PATH  [=  path  ]

将 path  参数设置为要在其中添加 .pgc 文件的目录路径。 例如，以下命令行将文件夹设置为 C:\profile：

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>请参阅

[按配置优化](profile-guided-optimizations.md)<br/>
[/GENPROFILE 和 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](reference/useprofile.md)<br/>
