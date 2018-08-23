---
title: 转换阶段 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- translation phases
- preprocessor, translation
- translation, compiler process
- preprocessor
- file translation [C++], compiler process
- files [C++], translation
ms.assetid: a7f7a8c9-e8ba-4321-9e50-ebfbbdcce9db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 172c7d755f0e7a7b8f2eb198d19775ffb0f2cc53
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538581"
---
# <a name="phases-of-translation"></a>转换阶段
C 和 C++ 程序包含一个或多个源文件，每个源文件包含程序的一些文本。 源文件与其包含文件（使用 `#include` 预处理器指令包含的文件），但不包含由条件编译指令（如 `#if`）删除的代码部分，一起称为“翻译单元”。  
  
可以在不同的时间翻译源文件 - 实际上，通常只翻译过期的文件。 翻译后的翻译单元可作为单独的对象文件或对象代码库处理。 然后，将这些单独的已翻译的翻译单元链接起来以构成可执行程序或动态链接库 (DLL)。  有关可用作链接器输入的文件的详细信息，请参阅[LINK 输入文件](../build/reference/link-input-files.md)。  
  
翻译单元可通过以下项进行通信：  
  
- 对具有外部链接的函数的调用。  
  
- 对具有外部链接的类成员函数的调用。  
  
- 对具有外部链接的对象的直接修改。  
  
- 对文件的直接修改。  
  
- 进程间通信（仅适用于基于 Microsoft Windows 的应用程序）。  
  
以下列表描述了编译器翻译文件的阶段：  
  
*字符映射*  
源文件中的字符将映射到内部源表示形式。 在此阶段，三元组序列将转换为单字符内部表示形式。  
  
*行拼接*  
以反斜杠结尾的所有行 (**\\**) 且后跟换行符字符加入形成逻辑行从物理行的源文件中的下一行。 除非源文件是空的，否则它必须以前面没有反斜杠的换行符结束。  
  
*词汇切分*  
源文件分为预处理标记和空白字符。 源文件中的注释将逐一替换为空白字符。 换行符将保留。  
  
*预处理*  
将执行预处理指令，并且宏将展开到源文件中。 `#include` 语句调用从所有包含的文本上的三个翻译步骤开始的翻译。  
  
*字符集映射*  
所有源字符集成员和转义序列将转换为执行字符集中的等效项。 对于 Microsoft C 和 C++，源和执行字符集都为 ASCII。  
  
*字符串串联*  
所有相邻字符串和宽字符串文本是串联的。 例如，将 `"String " "concatenation"` 变为 `"String concatenation"`。  
  
*翻译*  
将从语法和语义上分析所有标记；这些标记将转换为对象代码。  
  
*链接*  
解析所有外部引用以创建可执行程序或动态链接库。  
  
在遇到语法错误的翻译阶段，编译器会发出警告或错误。  
  
链接器会解析所有外部引用，并通过将一个或多个单独处理的翻译单元与标准库组合在一起来创建可执行程序或 DLL。  
  
## <a name="see-also"></a>请参阅  
 
[预处理器](../preprocessor/preprocessor.md)