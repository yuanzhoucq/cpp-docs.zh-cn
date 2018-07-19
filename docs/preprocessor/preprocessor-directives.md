---
title: 预处理器指令 |Microsoft 文档
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- directives, preprocessor
- preprocessor, directives
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5621c1a338ea6870d15dca65c303d4ac2bf8c7a
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122590"
---
# <a name="preprocessor-directives"></a>预处理器指令

预处理器指令，如`#define`和 **#ifdef**，通常用于简化源程序易于在不同的执行环境中编译和更改。 源文件中的指令告知预处理器执行特定操作。 例如，预处理器可以替换文本中的标记，将其他文件的内容插入源文件，或通过移除几个部分的文本来取消一部分文件的编译。 在扩展宏之前，将识别并执行预处理器行。 因此，如果宏扩展到类似于预处理器命令的内容，该预处理器无法识别此命令。

预处理器语句使用的字符集与源文件语句的相同，只不过转义序列不受支持。 预处理器语句中使用的字符集等同于[执行字符集](http://msdn.microsoft.com/en-us/a7901c61-524d-47c6-beb6-d9dacc2e72ed)。 预处理器还可识别负字符值。

预处理器可识别下列指令：

|||||
|-|-|-|-|
|[#define](../preprocessor/hash-define-directive-c-cpp.md)|[#error](../preprocessor/hash-error-directive-c-cpp.md)|[#import](../preprocessor/hash-import-directive-cpp.md)|[#undef](../preprocessor/hash-undef-directive-c-cpp.md)|
|[#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#include](../preprocessor/hash-include-directive-c-cpp.md)|[#using](../preprocessor/hash-using-directive-cpp.md)|
|[#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#line](../preprocessor/hash-line-directive-c-cpp.md)|[#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|
|[#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||

数字符号 (**#**) 必须是包含指令; 的行上的第一个非空白字符空白字符可以出现数字符号与指令的第一个字母之间。 某些指令包含自变量或值。 跟在指令 （除外的自变量或值是该指令的一部分） 的任何文本的前面必须有单行注释分隔符 (**//**) 或括在注释分隔符 ( __/\*\*/__).   包含预处理器指令的行可以继续通过字符前面，以反斜杠的结束行标记 (**\\**)。

预处理器指令可以出现在源文件中的任何位置，但是它们仅应用于源文件的剩余部分。

## <a name="see-also"></a>请参阅

[预处理器运算符](../preprocessor/preprocessor-operators.md)  
[预定义宏](../preprocessor/predefined-macros.md)  
[C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)  
