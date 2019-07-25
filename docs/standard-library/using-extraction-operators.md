---
title: 使用提取运算符
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 7950984973f8df236905128ce4b5336ecb874b7f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458042"
---
# <a name="using-extraction-operators"></a>使用提取运算符

提取运算符 (`>>`) 是从输入流对象获取字节的最简单方式，它已被预先编程用于所有标准 C++ 数据类型。

带格式的文本输入提取运算符使用空格分隔传入的数据值。 如果文本字段包含多个字或用逗号分隔数字，这种方式就很不方便。 在这种情况下，可使用一种替代方法：使用不带格式的输入成员函数 [istream::getline](../standard-library/basic-istream-class.md#getline) 读取包含空格的文本块，然后通过特殊函数分析此块。 另一种方法是通过 `GetNextToken` 等成员函数派生输入流类，它可调用 istream 成员以提取字符数据并设置格式。

## <a name="see-also"></a>请参阅

[输入流](../standard-library/input-streams.md)
