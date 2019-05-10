---
title: pgosweep
ms.date: 03/14/2018
helpviewer_keywords:
- pgosweep program
- profile-guided optimizations, pgosweep
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
ms.openlocfilehash: 3ba31671fc3794e1cc959d86d914ba1eef2e01e4
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64341188"
---
# <a name="pgosweep"></a>pgosweep

在按配置优化用于从正在运行的程序的配置文件的所有数据都写入到.pgc 文件。

## <a name="syntax"></a>语法

> **pgosweep** [*options*] *image* *pgcfile*

### <a name="parameters"></a>参数

*options*<br/>
（可选）有效值*选项*是：

- **/?** 或 **/help**显示帮助消息。

- **/noreset 清理**保留在运行时数据结构中的计数。

*image*<br/>
使用创建的.exe 或.dll 文件的完整路径[/GENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)， [/FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)，或[/ltcg: pginstrument](reference/ltcg-link-time-code-generation.md)选项。

*pgcfile*<br/>
此命令写入的位置的数据计数.pgc 文件。

## <a name="remarks"></a>备注

**Pgosweep**命令适用于使用生成的程序[/GENPROFILE 或 /FASTGENPROFILE](reference/genprofile-fastgenprofile-generate-profiling-instrumented-build.md)选项，或已弃用[/ltcg: pginstrument](reference/ltcg-link-time-code-generation.md)选项。 中断正在运行的程序，并将配置文件数据写入到新的.pgc 文件。 默认情况下，该命令将在每个写入操作后重置计数。 如果指定 **/noreset 清理**选项，该命令将记录的值，但不是会重置它们正在运行的程序。 此选项可以重复的数据在以后检索配置文件数据。

其他用途**pgosweep**是检索配置文件信息只是应用程序的正常操作。 例如，可以运行**pgosweep**后立即启动应用程序并放弃该文件。 这将删除与启动成本相关联的配置文件数据。 然后，可以运行**pgosweep**之前结束应用程序。 现在所收集的数据具有与程序交互的用户可以仅从时间的配置文件信息。

在命名.pgc 文件 (通过使用*pgcfile*参数) 可以使用标准格式，即*appname ！ n*.pgc。 如果你使用此格式，编译器会自动找到这些数据在 **/LTCG /USEPROFILE**或 **/ltcg: pgo**阶段。 如果不使用标准格式，则必须使用[pgomgr](pgomgr.md)要合并的.pgc 文件。

> [!NOTE]
> 只能从 Visual Studio 开发人员命令提示符启动此工具。 无法从系统命令提示符或文件资源管理器中启动它。

有关如何捕获可执行文件中的配置文件数据的信息，请参阅[PgoAutoSweep](pgoautosweep.md)。

## <a name="example"></a>示例

在此示例命令中， **pgosweep**写入 myapp!1.pgc myapp.exe 的当前配置文件信息。

`pgosweep myapp.exe myapp!1.pgc`

## <a name="see-also"></a>请参阅

[按配置文件优化](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
