---
title: NMAKE 选项 |Microsoft Docs
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
ms.openlocfilehash: 89f71bff1d8f64da2ad029e300fe2427235eac0a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894520"
---
# <a name="nmake-options"></a>NMAKE 选项

NMAKE 选项如下表所述。 选项的前面有反斜杠 （/） 或短划线 （-） 和不区分大小写。 使用[！CMDSWITCHES](../build/makefile-preprocessing-directives.md)更改生成文件中或在 Tools.ini 选项设置。

|选项|目标|
|------------|-------------|
|/ A|强制生成的所有计算目标，即使对于的依赖项未过期。 不会强制生成不相关的目标。|
|B &LT;/B|即使时间戳相等，则强制生成。 建议仅用于非常快的系统 （解析为两秒或更少）。|
|/C|取消显示默认输出，包括非致命 NMAKE 错误或警告，时间戳和 NMAKE 版权消息。 禁止显示警告由 /K.颁发|
|/D|目标不存在时，显示时间戳的每个计算目标和依赖项和一条消息。 用于与 /P 调试生成文件。 使用 **！CMDSWITCHES**设置或清除 /D 的生成文件的一部分。|
|/E|使生成文件宏定义进行重写环境变量。|
|/ERRORREPORT [NONE&AMP;#124;提示&AMP;#124;队列&AMP;#124;发送]|如果在运行时失败 nmake.exe，可以使用 /ERRORREPORT 有关这些内部错误向 Microsoft 发送信息。<br /><br /> /ERRORREPORT 的详细信息，请参阅[/errorReport （报告内部编译器错误）](../build/reference/errorreport-report-internal-compiler-errors.md)。|
|/F*文件名*|指定*文件名*作为生成文件。 之前的空格或制表符可以放置*文件名*。 指定每个生成文件 /F 一次。 若要提供生成从标准输入文件，为指定短划线 （-）*文件名*，日期和结束键盘输入按 F6 或 CTRL + Z。|
|/G|显示包含的生成文件 ！INCLUDE 指令。  请参阅[生成文件预处理指令](../build/makefile-preprocessing-directives.md)有关详细信息。|
|/HELP，/？|显示 NMAKE 命令行语法的简短摘要。|
|/I|将忽略所有命令中的退出代码。 若要设置或清除 /I 选项生成文件的一部分，使用 **！CMDSWITCHES**。 若要忽略的生成文件一部分的退出代码，请使用短划线 （-） 命令修饰符或[。忽略](../build/dot-directives.md)。 如果同时指定了将重写 /K。|
|/K|如果命令返回错误，将继续生成不相关的依赖项。 此外会发出警告并返回退出代码为 1。 默认情况下，如果任何命令返回非零退出代码，NMAKE 暂停。 从 /K 警告所抑制的 /C;/I 重写 /K，如果同时指定两者。|
|/N|显示，但不会执行命令;预处理命令执行。 不显示在递归 NMAKE 调用的命令。 可用于调试生成文件和检查时间戳。 若要设置或清除 /N 选项生成文件的一部分，使用 **！CMDSWITCHES**。|
|/NOLOGO|禁止显示 NMAKE 版权消息。|
|/P|显示的信息 (宏定义、 推理规则、 目标， [。后缀](../build/dot-directives.md)列表) 到标准输出，然后运行生成。 如果不存在任何生成文件或命令行目标，则只显示信息。 与 /d 选项一起使用来调试生成文件。|
|/Q|检查目标; 的时间戳不会运行生成。 如果任何目标不是，返回非零退出代码如果所有目标都是最新和非零退出代码。 预处理命令执行。 如果从批处理文件运行 NMAKE 非常有用。|
|/R|清除 **。后缀**列表，并忽略推理规则和 Tools.ini 文件中定义的或预定义的宏。|
|/S|取消显示执行的命令。 若要禁止显示生成文件的部分，使用**\@** 命令修饰符或[。无提示](../build/dot-directives.md)。 若要设置或清除 /S 选项生成文件的一部分，使用 **！CMDSWITCHES**。|
|/T|更新的命令行的目标 （或第一个生成文件目标） 的时间戳和执行预处理命令，但不会运行生成。|
|/U|必须与 /N.结合使用 转储内联 NMAKE 文件，以便 /N 输出可以用作一个批处理文件。|
|/X*文件名*|NMAKE 错误输出发送到发送*文件名*而不是标准错误。 之前的空格或制表符可以放置*文件名*。 若要将错误输出发送到标准输出中，指定短划线 （-） 用于*文件名*。 不会影响到标准错误命令的输出。|
|/Y|禁用批处理模式推理规则。 选中此选项后，所有批模式推理规则被都视为常规推理规则。|

## <a name="see-also"></a>请参阅

[运行 NMAKE](../build/running-nmake.md)
