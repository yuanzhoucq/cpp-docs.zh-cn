---
title: 编译器警告（等级 1）C4912
ms.date: 11/04/2016
f1_keywords:
- C4912
helpviewer_keywords:
- C4912
ms.assetid: ba1f1a66-8c20-4792-9ac8-43e49f729ae2
ms.openlocfilehash: 1e9e13cd909ec77397eac8b40ec4323b2b5847d9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050254"
---
# <a name="compiler-warning-level-1-c4912"></a>编译器警告（等级 1）C4912

“attribute”：在嵌套 UDT 上，特性有未定义的行为

可以忽略应用于嵌套 UDT（用户定义的类型，这可能为 typedef、union 或 struct）的特性。

下面的代码演示了将如何生成此警告：

```cpp
// C4912.cpp
// compile with: /W1
#include <windows.h>
[emitidl, module(name="xx")];

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface IMy
{
};

[coclass, default(IMy), appobject, uuid("00000000-0000-0000-0000-000000000001")]
class CMy : public IMy
{
   [export, v1_enum] typedef enum myEnum { k3_1 = 1, k3_2 = 2 } myEnumv;   // C4912
};
int main()
{
}
```