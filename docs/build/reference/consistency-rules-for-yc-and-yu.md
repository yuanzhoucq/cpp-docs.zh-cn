---
title: "/Yc 和 /Yu 的一致性规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/yc"
  - "/yu"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Yc 编译器选项 [C++]"
  - "/Yu 编译器选项 [C++]"
  - "Yc 编译器选项 [C++]"
  - "-Yc 编译器选项 [C++]"
  - "Yu 编译器选项 [C++]"
  - "-Yu 编译器选项 [C++]"
ms.assetid: 9dfb0e32-ec9b-4a36-9355-27a0e5fba512
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Yc 和 /Yu 的一致性规则
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当使用用 \/Yc 或 \/Yu 创建的预编译头时，编译器将当前编译环境与创建 .pch 文件时存在的编译环境进行比较。  确保为当前编译指定一个与前一个环境一致的环境（使用一致的编译器选项、杂注等）。  如果编译器检测到不一致性，它将发出警告并在其可能出现的地方标识该不一致性。  这些警告不一定表明 .pch 文件有问题；它们只是警告您可能存在冲突。  以下各节解释预编译头的一致性要求。  
  
## 编译器选项一致性  
 下表列出使用预编译头时可能触发不一致性警告的编译器选项。  
  
|选项|Name|规则|  
|--------|----------|--------|  
|\/D|定义常数和宏|在创建预编译头的编译与当前编译之间必须相同。  不检查已定义常数的状态，但如果文件依赖于已改变常数的值，则会产生不可预知的结果。|  
|\/E 或 \/EP|将预处理器输出复制到标准输出|预编译头不适用于 \/E 或 \/EP 选项。|  
|\/Fr 或 \/FR|生成 Microsoft 源浏览器信息|为使 \/Fr 和 \/FR 选项可与 \/Yu 选项一起使用，在创建预编译头时它们同样必须已生效。  后面使用预编译头的编译也生成源浏览器信息。  浏览器信息放置在单个 .sbr 文件中，并由其他文件以引用 CodeView 信息的方式引用。  无法重写源浏览器信息的位置。|  
|\/GA、\/GD、\/GE、\/Gw 或 \/GW|Windows 协议选项|在创建预编译头的编译与当前编译之间必须相同。  如果这些选项不同，将产生错误信息。|  
|\/Zi|生成完整的调试信息|如果在创建预编译头时此选项有效，则后面使用预编译的编译就可以使用调试信息。  如果在创建预编译头时 \/Zi 无效，则后面使用预编译和 \/Zi 选项的编译将触发警告。  调试信息放置在当前对象文件中，并且预编译头中定义的本地符号对调试器不可用。|  
  
> [!NOTE]
>  预编译头功能仅应用于具有 C 和 C\+\+ 源文件的文件。  
  
## 包含路径一致性  
 用 \/Yc 创建的预编译头不包含有关在创建 .pch 文件时有效的包含路径的信息。  使用 .pch 文件时，编译器总是使用当前编译中指定的包含路径。  
  
## 源文件一致性  
 使用预编译头时，编译器将忽略所有在 hdrstop 杂注前出现的预处理器指令（包括杂注）。  由这些预处理器指令指定的编译必须与用于创建预编译头文件的编译相同。  
  
## 杂注一致性  
 在对预编译头进行编译的过程中所处理的杂注通常会影响后面使用此预编译头的文件。  下列杂注只影响 .pch 文件中的代码；它们不影响后面使用该 .pch 文件的代码：  
  
||||  
|-|-|-|  
|注释|page|subtitle|  
|Linesize|pagesize|标题|  
|消息|skip||  
  
 下列杂注保留为预编译头的一部分，并且影响使用该预编译头的编译的其余部分：  
  
||||  
|-|-|-|  
|alloc\_text|function|optimize|  
|auto\_inline|inline\_depth|pack|  
|check\_pointer|inline\_recursion|same\_seg|  
|check\_stack|intrinsic|warning|  
|code\_seg|loop\_opt||  
|data\_seg|native\_caller||  
  
## 请参阅  
 [预编译头一致性规则](../../build/reference/precompiled-header-consistency-rules.md)   
 [\/Yc（创建预编译的头文件）](../../build/reference/yc-create-precompiled-header-file.md)   
 [\/Yu（使用预编译的头文件）](../../build/reference/yu-use-precompiled-header-file.md)