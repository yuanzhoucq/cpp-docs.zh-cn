---
title: "NMAKE 选项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 程序, 选项"
ms.assetid: 00ba1aec-ef27-44cf-8d82-c5c095e45bae
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# NMAKE 选项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表描述了 NMAKE 选项。  选项前有斜杠 \(\/\) 或短划线 \(\-\)，并且不区分大小写。  使用 [\!CMDSWITCHES](../build/makefile-preprocessing-directives.md) 更改生成文件或 Tools.ini 中的选项设置。  
  
|选项|用途|  
|--------|--------|  
|\/A|强制生成所有已评估的目标，即使这些目标相对于依赖项未过期。  不强制不相关目标的生成。|  
|\/B|即使时间戳相等，也强制生成。  建议只用于非常快的系统（解析为两秒或小于两秒）。|  
|\/C|取消默认输出，包括非致命的 NMAKE 错误或警告、时间戳以及 NMAKE 版权信息。  取消 \/K 选项发出的警告。|  
|\/D|当目标不存在时，显示每个已评估的目标、依赖项和消息的时间戳。  与 \/P 选项一起用于调试生成文件。  使用 **\!CMDSWITCHES** 设置或清除部分生成文件的 \/D 选项。|  
|\/E|使环境变量重写生成文件宏定义。|  
|\/ERRORREPORT\[NONE &#124; PROMPT &#124; QUEUE &#124; SEND \]|如果 nmake.exe 在运行时失败，则可以使用 \/ERRORREPORT 将有关这些内部错误的信息发送给 Microsoft。<br /><br /> 有关 \/ERRORREPORT 的更多信息，请参见 [\/errorReport（报告内部编译器错误）](../build/reference/errorreport-report-internal-compiler-errors.md)。|  
|\/F `filename`|将 `filename` 指定为生成文件。  空格或制表符可以位于 `filename` 的前面。  为每个生成文件指定一次 \/F 选项。  若要从标准输入提供生成文件，请为 `filename` 指定短划线 \(\-\)，并按 F6 或 Ctrl\+Z 结束键盘输入。|  
|\/G|显示 \!INCLUDE 指令中包含的生成文件。有关更多信息，请参见[生成文件预处理指令](../build/makefile-preprocessing-directives.md)。|  
|\/HELP, \/?|显示 NMAKE 命令行语法的简短摘要。|  
|\/I|忽略所有命令的退出代码。  若要设置或清除部分生成文件的 \/I 选项，请使用 **\!CMDSWITCHES**。  若要忽略部分生成文件的退出代码，请使用短划线 \(\-\) 命令修饰符或 [.IGNORE](../build/dot-directives.md)。  如果两者都指定了，则重写 \/K 选项。|  
|\/K|如果命令返回错误，则继续生成不相关的依赖项。  同时发出警告并返回退出代码 1。  默认情况下，如果有任一命令返回非零退出代码，NMAKE 将暂停。  来自 \/K 选项的警告被 \/C 选项取消；如果两者都指定了，则 \/I 选项重写 \/K 选项。|  
|\/N|显示但不执行命令；执行预处理命令。  不在递归 NMAKE 调用中显示命令。  对于调试生成文件和检查时间戳很有用。  若要设置或清除部分生成文件的 \/N 选项，请使用 **\!CMDSWITCHES**。|  
|\/NOLOGO|取消 NMAKE 版权消息。|  
|\/P|显示标准输出的信息（宏定义、推理规则、目标、[.SUFFIXES](../build/dot-directives.md) 列表），然后运行生成。  如果不存在任何生成文件和命令行目标，则只显示信息。  与 \/D 选项一起用于调试生成文件。|  
|\/Q|检查目标的时间戳；不运行生成。  如果所有目标都是最新的，则返回零退出代码；如果有任何目标不是最新的，则返回非零退出代码。  执行预处理命令。  从批处理文件运行 NMAKE 时很有用。|  
|\/R|清除 **.SUFFIXES** 列表并忽略在 Tools.ini 文件中定义的或预定义的推理规则和宏。|  
|\/S|取消已执行命令的显示。  若要禁止部分生成文件中的显示，请使用 **@** 命令修饰符或 [.SILENT](../build/dot-directives.md)。  若要设置或清除部分生成文件的 \/S 选项，请使用 **\!CMDSWITCHES**。|  
|\/T|更新命令行目标（或第一个生成文件目标）的时间戳并执行预处理命令，但不运行生成。|  
|\/U|必须与 \/N 选项一起使用。  转储内联 NMAKE 文件，以便 \/N 输出可用作批处理文件。|  
|\/X `filename`|将 NMAKE 错误输出发送到 `filename` 而不是标准错误。  空格或制表符可以位于 `filename` 的前面。  若要将错误输出发送到标准输出，请为 `filename` 指定短划线 \(\-\)。  不影响从命令到标准错误的输出。|  
|\/Y|禁用批模式推理规则。  选定该选项后，所有批模式推理规则被视为常规推理规则。|  
  
## 请参阅  
 [运行 NMAKE](../build/running-nmake.md)