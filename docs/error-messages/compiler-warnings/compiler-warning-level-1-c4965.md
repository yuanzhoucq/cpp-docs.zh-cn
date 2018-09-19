---
title: 编译器警告 （等级 1） C4965 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4965
dev_langs:
- C++
helpviewer_keywords:
- C4965
ms.assetid: 47f3f6dc-459b-4a25-9947-f394c8966cb5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8613585d1f34060fb2e60f976f76c6801005aca
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036639"
---
# <a name="compiler-warning-level-1-c4965"></a>编译器警告（等级 1）C4965

整数 0; 的隐式装箱请使用 nullptr 或显式强制转换

Visual c + + 功能值类型隐式的装箱。 现在使用的 c + + 托管扩展分配空值会导致指令将成为赋值为装箱的整数。

有关详细信息，请参阅[装箱](../../windows/boxing-cpp-component-extensions.md)。

## <a name="example"></a>示例

下面的示例生成 C4965。

```
// C4965.cpp
// compile with: /clr /W1
int main() {
   System::Object ^o = 0;   // C4965

   // the previous line is the same as the following line
   // using Managed Extensions for C++
   // System::Object *o = __box(0);

   // OK
   System::Object ^o2 = nullptr;
   System::Object ^o3 = safe_cast<System::Object^>(0);
}
```