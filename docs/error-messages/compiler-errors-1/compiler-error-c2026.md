---
title: 编译器错误 C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208060"
---
# <a name="compiler-error-c2026"></a>编译器错误 C2026

字符串太大，已截断尾部字符

字符串的长度超过16380个单字节字符的限制。

在连接相邻的字符串之前，字符串长度不能超过16380个单字节字符。

此长度约为一半的 Unicode 字符串也会生成此错误。

如果有一个定义如下的字符串，则会生成 C2026：

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

您可以按如下所示对其进行分解：

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

您可能想要在自定义资源或外部文件中存储非常大的字符串文本（32K 或更多）。 有关详细信息，请参阅[创建新的自定义资源或数据资源](../../windows/creating-a-new-custom-or-data-resource.md)。
