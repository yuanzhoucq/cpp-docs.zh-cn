---
title: 编译器错误 C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: da4c03c681f95efaa5edb159869315b41d027e99
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303523"
---
# <a name="compiler-error-c2026"></a>编译器错误 C2026

字符串太大，已截断尾部字符

字符串的长度超出 16380 单字节字符的限制。

之前在连接的相邻字符串，不能大于 16380 单字节字符字符串。

此长度大约一半的 Unicode 字符串还会生成此错误。

如果必须按如下所示定义的字符串，则会生成 C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

您可以将其分解，如下所示：

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

您可能想要存储特别大的字符串文本 （32k 个或多个） 自定义资源或外部文件中。 请参阅[创建新的自定义资源或数据资源](../../windows/creating-a-new-custom-or-data-resource.md)有关详细信息。