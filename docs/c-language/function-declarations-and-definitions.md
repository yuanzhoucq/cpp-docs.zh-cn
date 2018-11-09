---
title: 函数声明和定义
ms.date: 11/04/2016
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
ms.openlocfilehash: 1f533bad308a9bc892bfe928b581c4b7197cf6f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624024"
---
# <a name="function-declarations-and-definitions"></a>函数声明和定义

函数原型确定了函数的名称、返回类型以及形参的类型和数量。 函数定义包括函数体。

## <a name="remarks"></a>备注

函数声明和变量声明均可出现在函数定义的内部或外部。 函数定义中的所有声明应在“内部”或“局部”级别显示。 所有函数定义之外的声明应在“外部”、“全局”或“文件范围”级别显示。 变量定义（如声明）可在内部级别（在函数定义中）或在外部级别（在所有函数定义外）显示。 函数定义始终会在外部级别显示。 [函数定义](../c-language/c-function-definitions.md)中进一步讨论了函数定义。 [函数原型](../c-language/function-prototypes.md)中介绍了函数原型。

## <a name="see-also"></a>请参阅

[源文件和源程序](../c-language/source-files-and-source-programs.md)