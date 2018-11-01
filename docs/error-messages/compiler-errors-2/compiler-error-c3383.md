---
title: 编译器错误 C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: 38aea188eeac90cd23d9203a53b4e630be2f115b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428010"
---
# <a name="compiler-error-c3383"></a>编译器错误 C3383

不支持将“operator new”与 /clr:safe 一起使用

**/clr:safe** 编译的输出文件可确保是类型安全的，且不支持指针。

有关详细信息，请参阅

- [/cgthreads（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)

- [Visual C++ 64 位迁移的常见问题](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>示例

下面的示例生成 C3383。

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```