---
title: 编译器警告 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: d604c234b9445a7e5304118124620f0057f30975
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311340"
---
# <a name="compiler-warning-c4439"></a>编译器警告 C4439

function： 函数签名中的托管类型的定义必须具有 __clrcall 调用约定

编译器隐式替换调用约定，具有[__clrcall](../../cpp/clrcall.md)。 若要解决此警告，请删除`__cdecl`或`__stdcall`调用约定。

C4439 始终作为错误发出。 您可以关闭此警告，其中包含`#pragma warning`或 **/wd**; 请参阅[警告](../../preprocessor/warning.md)或[/w、 /W0、 /W1、 /W2、 /W3、 / w4、 /w1、 /w2、 /w3、 /w4、 /Wall、 /wd、 / /we、 /wo、 /Wv、 /WX （警告级别）](../../build/reference/compiler-option-warning-level.md)有关详细信息。

## <a name="example"></a>示例

下面的示例生成 C4439。

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```