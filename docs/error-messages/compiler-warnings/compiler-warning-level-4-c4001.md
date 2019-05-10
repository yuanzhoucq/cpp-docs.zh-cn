---
title: 编译器警告 （等级 C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: dd18dc27ee13eab05ea0253c8ebcc990105c15c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401483"
---
# <a name="compiler-warning-level-4-c4001"></a>编译器警告 （等级 C4001

使用了非标准扩展 single line comment

> [!NOTE]
> Visual Studio 2017 版本 15.5 中删除了此警告，因为单行注释是在 C99 标准。

单行注释都是标准的C++和在 C 开头 C99 标准。
在严格 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))，包含单行注释的 C 文件生成 C4001 由于使用了非标准扩展的使用情况。 因为单行注释都是标准的C++、 C 文件包含单行注释不会生成 C4001 和 Microsoft 扩展 (/Ze) 编译时。

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