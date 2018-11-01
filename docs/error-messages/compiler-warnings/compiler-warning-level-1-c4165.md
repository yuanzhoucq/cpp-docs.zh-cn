---
title: 编译器警告 （等级 1） C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: 4d6377730e262efafb38f5e714989e9075a77a04
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534376"
---
# <a name="compiler-warning-level-1-c4165"></a>编译器警告 （等级 1） C4165

HRESULT 正在转换为 bool;是否确定这是你想？

使用中的 HRESULT 时[如果](../../cpp/if-else-statement-cpp.md)语句，HRESULT 将转换为[bool](../../cpp/bool-cpp.md)除非您显式地测试作为 HRESULT 的变量。 默认情况下，此警告处于关闭状态。

## <a name="example"></a>示例

下面的示例生成 C4165

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```