---
title: pgosweep |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9680dc47d850bd49eff343c0e382b7132697858d
ms.sourcegitcommit: ee7d74683af7631441c8c7f65ef5ceceaee4a5ee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="pgosweep"></a>pgosweep

使用按配置优化以从正在运行的程序的所有配置文件数据写入到对应的.pgc 文件。

## <a name="syntax"></a>语法

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>参数

*选项*（可选）<br/>
有效值*选项*是：

- **/?** 或**/帮助**显示帮助消息。

- **/noreset**保留的运行时数据结构中的计数。

*image*<br/>
通过使用创建的.exe 或.dll 文件的完整路径[/GENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)， [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)，或[/ltcg: pginstrument](ltcg-link-time-code-generation.md)选项。

*pgcfile*<br/>
此命令写入的位置出的数据计数.pgc 文件。

## <a name="remarks"></a>备注

**Pgosweep**命令适用于使用生成的程序[/GENPROFILE 或 /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)选项，或不推荐使用[/ltcg: pginstrument](ltcg-link-time-code-generation.md)选项。 中断正在运行的程序，并将配置文件数据写入新的.pgc 文件。 默认情况下，该命令将在每个写入操作后重置计数。 如果指定**/noreset**选项，该命令将记录的值，但不是会重置它们正在运行的程序。 此选项使重复数据，如果你稍后检索该配置文件数据。

其他用途**pgosweep**是检索仅针对应用程序的正常操作的配置文件信息。 例如，可以运行**pgosweep**后很快启动应用程序并丢弃该文件。 这将删除与启动成本关联的配置文件数据。 然后，可以运行**pgosweep**结束应用程序之前。 现在所收集的数据具有用户可与程序交互的配置文件信息只能从时间。

当名称对应的.pgc 文件 (通过使用*pgcfile*参数) 可以使用标准的格式，这是*appname ！ n*.pgc。 如果你使用此格式，则编译器自动找到该数据在**/LTCG /USEPROFILE**或**/ltcg: pgo**阶段。 如果不使用标准的格式，则必须使用[pgomgr](pgomgr.md)以合并.pgc 文件。

> [!NOTE]
> 只能从 Visual Studio 开发人员命令提示，可以启动此工具。 不能从系统命令提示符或从文件资源管理器启动此工具。

有关如何捕获从内可执行文件的配置文件数据的信息，请参阅[PgoAutoSweep](pgoautosweep.md)。

## <a name="example"></a>示例

在此示例命令中， **pgosweep**写入 myapp!1.pgc myapp.exe 的当前配置文件信息。

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>请参阅

[按配置文件优化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
