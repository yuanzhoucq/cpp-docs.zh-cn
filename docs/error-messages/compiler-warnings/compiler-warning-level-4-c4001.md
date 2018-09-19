---
title: 编译器警告 （等级 C4001 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c325656b9e61ee324a3b9f171413f1020440f9ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025407"
---
# <a name="compiler-warning-level-4-c4001"></a>编译器警告 （等级 C4001

使用了非标准扩展 single line comment

> [!NOTE]
> Visual Studio 2017 版本 15.5 中删除了此警告，因为单行注释是在 C99 标准。

单行注释是标准 c + + 中和在 C 开头 C99 标准。
在严格 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，包含单行注释的 C 文件生成 C4001 由于使用了非标准扩展的使用情况。 因为单行注释是标准 c + + 中，C 文件包含单行注释不生成 C4001 和 Microsoft 扩展 (/Ze) 编译时。

## <a name="example"></a>示例

若要禁用警告，请取消注释[#pragma warning(disable:4001)](../../preprocessor/warning.md)。

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```