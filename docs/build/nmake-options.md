---
title: NMAKE 选项 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, options
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2f7ad294a9f199d5dbe6821c61317ed0b6b2693
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="nmake-options"></a>NMAKE 选项
下表描述了 NMAKE 选项。 选项都以斜杠 （/） 或短划线 （-） 和不区分大小写。 使用[！CMDSWITCHES](../build/makefile-preprocessing-directives.md)更改生成文件中或在 Tools.ini 选项设置。  
  
|选项|目标|  
|------------|-------------|  
|/ A|强制生成的所有计算目标，即使对于的依赖项不过期。 不会强制生成不相关的目标。|  
|/ B|即使时间戳相等，则强制生成。 建议只用于非常快系统 （解决方法的两个秒或更少）。|  
|/C|禁止显示默认输出，包括非致命 NMAKE 错误或警告、 时间戳，和 NMAKE 版权消息。 禁止显示警告签发 /K.|  
|/D|显示评估时间戳的每个目标、 依赖项和一条消息时目标不存在。 用于与/P 调试生成文件。 使用**！CMDSWITCHES**设置或清除文件的生成文件的一部分 /D 选项。|  
|/E|要生成文件宏定义进行重写的原因环境变量。|  
|/ERRORREPORT [NONE&AMP;#124;提示&AMP;#124;队列&AMP;#124;发送]|如果在运行时失败 nmake.exe，你可以使用 /ERRORREPORT 信息向 Microsoft 发送有关这些内部错误。<br /><br /> /ERRORREPORT 有关的详细信息，请参阅[/errorReport （报告内部编译器错误）](../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|/F `filename`|指定`filename`作为生成文件。 空格或选项卡可以在前面`filename`。 指定 /F 一次为每个生成文件。 若要提供生成从标准输入文件，为指定短划线 （-） `filename`，日期和结束按 F6 或 CTRL + Z 的键盘输入。|  
|/G|显示包含的生成文件 ！INCLUDE 指令。  请参阅[生成文件预处理指令](../build/makefile-preprocessing-directives.md)有关详细信息。|  
|/ 帮助，/？|显示 NMAKE 命令行语法的简短摘要。|  
|/I|将忽略所有命令的退出代码。 若要设置或清除 /I 选项的生成文件的一部分，使用**！CMDSWITCHES**。 若要忽略的生成文件的一部分的退出代码，请使用短划线 （-） 命令修饰符或[。忽略](../build/dot-directives.md)。 如果同时指定了重写 /k 选项。|  
|/K|继续生成不相关的依赖项，如果命令会返回错误。 此外会发出警告，并返回的退出代码为 1。 默认情况下，如果任何命令返回非零退出代码，将暂停 NMAKE。 从 /K 警告所抑制的 /C;如果同时指定了，/I 重写 /k 选项。|  
|/N|显示，但不会执行命令;预处理命令执行。 未在递归 NMAKE 调用中显示命令。 可用于调试生成文件和检查时间戳。 若要设置或清除 /N 选项生成文件的一部分，使用**！CMDSWITCHES**。|  
|/NOLOGO|禁止 NMAKE 版权信息。|  
|/P|显示的信息 (宏定义、 推理规则、 目标， [。后缀](../build/dot-directives.md)列表) 到标准输出，然后运行生成。 如果不存在任何生成文件或命令行目标，则只显示信息。 与 /d 选项一起使用，来调试生成文件。|  
|/Q|检查目标; 的时间戳不运行生成。 如果任何目标，则不，返回零退出代码如果所有目标都是最新，则为非 0 退出代码。 预处理命令执行。 如果从批处理文件运行 NMAKE 非常有用。|  
|/R|清除**。后缀**列表，并忽略推理规则和 Tools.ini 文件中定义的或预定义的宏。|  
|/S|取消显示执行命令。 若要禁止显示生成文件的部分，使用**@** 命令修饰符或[。无提示](../build/dot-directives.md)。 若要设置或清除 /S 选项生成文件的一部分，使用**！CMDSWITCHES**。|  
|/T|更新时间戳的命令行的目标 （或第一个生成文件目标） 和执行预处理命令，但不运行生成。|  
|/U|必须与 /N.结合使用 转储内联 NMAKE 文件，以便 /N 输出可用作批处理文件。|  
|/X `filename`|将发送到 NMAKE 错误输出`filename`而不是标准错误。 空格或选项卡可以在前面`filename`。 若要将错误输出发送到标准输出中，为指定短划线 （-） `filename`。 不会影响到标准错误来自命令的输出。|  
|/Y|禁用批模式推理规则。 选中此选项后，所有批模式推理规则将被都视为常规推理规则。|  
  
## <a name="see-also"></a>请参阅  
 [运行 NMAKE](../build/running-nmake.md)