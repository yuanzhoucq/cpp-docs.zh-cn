---
title: 按配置优化的环境变量 |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- profile-guided optimizations, environment variables
ms.assetid: f95a6d1e-49a4-4802-a144-092026b600a3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 701f0292d9960801139abc698946122718247645
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="environment-variables-for-profile-guided-optimizations"></a>用于按配置文件优化的环境变量

有三个影响与创建的映像上的测试方案的环境变量**/ltcg: pgi**用于按配置文件优化的：

- **PogoSafeMode**指定是否使用快速模式或安全模式的应用程序分析。

- **VCPROFILE_ALLOC_SCALE**中添加其他内存以供探查器。

- **VCPROFILE_PATH**允许你指定用于.pgc 文件的文件夹。

**启动 Visual Studio 2015 中被弃用 PogoSafeMode 和 VCPROFILE_ALLOC_SCALE 环境变量。** 链接器选项[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)和[/USEPROFILE](useprofile.md)作为这些环境变量指定相同的链接器行为。

## <a name="pogosafemode"></a>PogoSafeMode

已弃用此环境变量。 使用**EXACT**或**NOEXACT**自变量**/GENPROFILE**或**/FASTGENPROFILE**来控制此行为。

清除或设置**PogoSafeMode**环境变量以指定是否要用于快速模式或安全模式的应用程序分析在 x86 系统。

按配置优化 (PGO) 的分析阶段有两种可能的模式：*快速模式*和*安全模式下*。 分析在快速模式下时，它使用**INC**指令来增加数据计数器。 **INC**指令速度更快，但不是线程安全。 分析在安全模式下时，它使用**锁 INC**指令来增加数据计数器。 **锁 INC**指令具有相同的功能**INC**指令，并且是线程安全的但它是低于**INC**指令。

默认情况下，PGO 分析会在运行快速模式。 **PogoSafeMode**是仅需要你想要使用安全模式。

若要运行 PGO 分析在安全模式下，必须使用环境变量**PogoSafeMode**或链接器开关**/PogoSafeMode**，取决于系统。 如果你正在执行分析在 x64 计算机，你必须使用链接器开关。 如果你正在执行分析 x86 计算机，你可以使用链接器切换或设置**PogoSafeMode**为之前启动优化过程的任何值的环境变量。

### <a name="pogosafemode-syntax"></a>PogoSafeMode 语法

> **set PogoSafeMode**[**=**_value_]

设置**PogoSafeMode**为任何值，以启用安全模式。 设置要清除以前的值并重新启用快速模式下的值。

## <a name="vcprofileallocscale"></a>VCPROFILE_ALLOC_SCALE

已弃用此环境变量。 使用**MEMMIN**和**MEMMAX**自变量**/GENPROFILE**或**/FASTGENPROFILE**来控制此行为。

修改**VCPROFILE_ALLOC_SCALE**环境变量，若要更改的内存量分配为保存配置文件数据。 在极少数情况下，将不会有足够的内存可用于支持运行测试方案时收集配置文件数据。 在这些情况下，你可以通过设置中增加的内存量**VCPROFILE_ALLOC_SCALE**。 如果测试运行，该值指示你没有足够的内存期间收到一条错误消息，将分配到更大的值**VCPROFILE_ALLOC_SCALE**，直到在测试运行完成，但没有内存不足错误。

### <a name="vcprofileallocscale-syntax"></a>VCPROFILE_ALLOC_SCALE 语法

> **set VCPROFILE_ALLOC_SCALE**[__=__*scale_value*]

*Scale_value*参数是用于运行测试方案所需的内存容量一个比例因子。  默认值为 1。 例如，此命令行设置的缩放比例为 2:

`set VCPROFILE_ALLOC_SCALE=2`

## <a name="vcprofilepath"></a>VCPROFILE_PATH

使用**VCPROFILE_PATH**环境变量以指定要创建对应的.pgc 文件的目录。 默认情况下，在所分析二进制文件所在的目录中创建对应的.pgc 文件。 但是，如果二进制文件的绝对路径不存在，可能出现此情况，在其中生成二进制文件已从其他计算机上运行配置文件方案时，你可以设置**VCPROFILE_PATH**到目标计算机存在的路径。

### <a name="vcprofilepath-syntax"></a>VCPROFILE_PATH 语法

> **set VCPROFILE_PATH**[**=**_path_]

设置*路径*到要在其中添加.pgc 文件的目录路径的参数。 例如，此命令行 C:\profile 到设置的文件夹：

`set VCPROFILE_PATH=c:\profile`

## <a name="see-also"></a>请参阅

[按配置文件优化](../../build/reference/profile-guided-optimizations.md)<br/>
[/GENPROFILE 和 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)<br/>
[/USEPROFILE](useprofile.md)<br/>
