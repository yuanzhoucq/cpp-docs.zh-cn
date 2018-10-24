---
title: C 加法运算符 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- usual arithmetic conversions
- operators [C], addition
- + operator, additive operators
- additive operators
- arithmetic operators [C++], additive operators
ms.assetid: bb8ac205-b061-41fc-8dd4-dab87c8b900c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 339904e3fe75c712254f3a7802fc76a0e283c8e5
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808350"
---
# <a name="c-additive-operators"></a>C 加法运算符

加法运算符执行加法 (**+**) 和减法 (**-**) 运算。

## <a name="syntax"></a>语法

*additive-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **+** *multiplicative-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*additive-expression* **-** *multiplicative-expression*

> [!NOTE]
> 虽然 *additive-expression* 的语法包括 *multiplicative-expression*，但这并不表示需要使用乘法表达式。 对于 *multiplicative-expression*、*cast-expression* 和 *unary-expression*，请参阅 [C 语言语法摘要](../c-language/c-language-syntax-summary.md)中的语法。

操作数可以是整型值或浮点值。 还可以对指针值执行一些加法运算，如针对每个运算符的讨论中所述。

相加运算符对整型和浮点型操作数执行常用算术转换。 结果的类型是转换后操作数的类型。 由于相加运算符执行的转换不提供溢出或下溢条件，因此，如果在转换后，无法用操作数类型表示加法运算的结果，则信息可能会丢失。

## <a name="see-also"></a>请参阅

[加法运算符：+ 和 -](../cpp/additive-operators-plus-and.md)