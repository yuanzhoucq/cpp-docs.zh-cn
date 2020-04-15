---
title: 预处理器
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
ms.assetid: e120eda3-b413-49f1-a07c-e9fb128cf500
ms.openlocfilehash: 7188d7a6803c9eec109a59906cf0c016a460819d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337515"
---
# <a name="preprocessor"></a>预处理器

预处理器是将源文件的文本作为翻译的第一阶段操作的文本处理器。 预处理器不解析源文本，但它确实将其分解为令牌以查找宏调用。 尽管编译器一般会在其第一个传递中调用预处理器，但还是可以为了在不进行编译的情况下处理文本而单独调用预处理器。

预处理器的参考材料包括下列部分：

- [预处理器指令](../preprocessor/preprocessor-directives.md)

- [前处理器运算符](../preprocessor/preprocessor-operators.md)

- [预定义宏](../preprocessor/predefined-macros.md)

- [杂注](../preprocessor/pragma-directives-and-the-pragma-keyword.md)

**微软特定**

您可以使用[/E](../build/reference/e-preprocess-to-stdout.md)或[/EP](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)编译器选项在预处理后获取源代码的列表。 这两个选项都调用预处理器并将生成的文本发送到标准输出设备，在大多数情况下，标准输出设备是控制台。 这两个选项之间的区别在于包含`/E``#line`指令，并`/EP`剥离这些指令。

**结束微软特定**

## <a name="special-terminology"></a><a name="_predir_special_terminology"></a>特殊术语

在预处理器文档中，术语“自变量”指传递给函数的实体。 在某些情况下，它由"实际"或"正式"修改，分别描述函数调用中指定的参数表达式和函数定义中指定的参数声明。

术语“变量”指简单的 C 类型数据对象。 术语"对象"是指C++对象和变量;这是一个包容性的术语。

## <a name="see-also"></a>另请参阅

[C/C++预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)\
[翻译阶段](../preprocessor/phases-of-translation.md)
