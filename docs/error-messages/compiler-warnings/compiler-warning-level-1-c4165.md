---
title: 编译器警告 （等级 1） C4165 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4165
dev_langs:
- C++
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c532ddee7a2066190c2f926ba7b1240c0418f6c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084921"
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