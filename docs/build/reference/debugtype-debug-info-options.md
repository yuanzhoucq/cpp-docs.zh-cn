---
title: -DEBUGTYPE （调试信息选项） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1255c92a7de4a0f1707cd20f91e8b9f1de640942
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440454"
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE（调试信息选项）

/DEBUGTYPE 选项指定 /DEBUG 选项生成的调试信息的类型。

```
/DEBUGTYPE:[CV | PDATA | FIXUP]
```

## <a name="arguments"></a>自变量

**CV**<br/>
指示链接器针对 PDB 文件中的符号、行号和其他对象编译信息发出调试信息。 默认情况下启用此选项时 **/debug**指定并 **/DEBUGTYPE**未指定。

**PDATA**<br/>
指示链接器向 PDB 文件中的调试流信息添加 .pdata 和 .xdata 条目。 默认情况下启用此选项时同时 **/debug**并 **/DRIVER**所指定的选项。 如果 **/DEBUGTYPE:PDATA**指定其本身而言，链接器会自动将包含调试符号在 PDB 文件中的。 如果 **/DEBUGTYPE:PDATA，修正**指定，则链接器不包括调试符号在 PDB 文件中的。

**链接地址信息**<br/>
指示链接器向 PDB 文件中的调试流信息添加重定位表条目。 默认情况下启用此选项时同时 **/debug**并 **/profile**所指定的选项。 如果 **/DEBUGTYPE:FIXUP**或 **/DEBUGTYPE:FIXUP，PDATA**指定，则链接器不包括调试符号在 PDB 文件中的。

自变量 **/DEBUGTYPE**可能按任何顺序组合并用逗号分隔。 **/DEBUGTYPE**选项和其参数不区分大小写。

## <a name="remarks"></a>备注

使用 **/DEBUGTYPE**选项以指定在调试流中包含重定位表数据或.pdata 和.xdata 标头信息。 这导致链接器包含有关破坏内核模式代码时内核调试程序中可见的用户模式代码的信息。 若要使调试符号可用时**修正**是指定，包括**CV**参数。

若要调试代码在用户模式下，这是典型的应用程序， **/DEBUGTYPE**选项不需要。 默认情况下，输出指定调试编译器开关 ([/Z7、 /Zi、 /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) 发出所有信息需要由 Visual Studio 调试器。 使用 **/DEBUGTYPE:PDATA**或 **/debugtype: cv，PDATA，修正**结合了用户模式和内核模式组件，如设备驱动程序的配置应用程序的代码进行调试。 有关内核模式调试程序的详细信息，请参阅[调试工具的 Windows （WinDbg、 KD、 CDB、 NTSD）](/windows-hardware/drivers/debugger/index)

## <a name="see-also"></a>请参阅

[/DEBUG（生成调试信息）](../../build/reference/debug-generate-debug-info.md)<br/>
[/DRIVER（Windows NT 内核模式驱动程序）](../../build/reference/driver-windows-nt-kernel-mode-driver.md)<br/>
[/PROFILE（性能工具探查器）](../../build/reference/profile-performance-tools-profiler.md)<br/>
[（WinDbg、 KD、 CDB、 NTSD） 的 Windows 调试工具](/windows-hardware/drivers/debugger/index)