---
title: 编译器警告（等级2） C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: d685f1f40826b975623dbedc2ba8115c6b3edc45
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052183"
---
# <a name="compiler-warning-level-2-c4099"></a>编译器警告（等级2） C4099

"identifier"：首次使用 "objecttype1" 查看的类型名称，现在使用 "objecttype2"

声明为结构的对象被定义为类，或者声明为类的对象定义为结构。 编译器使用定义中给定的类型。

## <a name="example"></a>示例

下面的示例生成 C4099。

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```