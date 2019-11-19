---
title: 编译器警告 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 7cab2e55fca640438051fbb79ac933e83d5f3cbb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623656"
---
# <a name="compiler-warning-c4439"></a>编译器警告 C4439

"function"：签名中具有托管类型的函数定义必须具有 __clrcall 调用约定

编译器隐式地使用[__clrcall](../../cpp/clrcall.md)替换调用约定。 若要解决此警告，请删除 `__cdecl` 或 `__stdcall` 调用约定。

C4439 始终作为错误发出。 你可以通过 `#pragma warning` 或 **/wd**关闭此警告;有关详细信息，请参阅[警告](../../preprocessor/warning.md)或[/w、/W0、/W1、/W2、/W3、/W4、/W1、/W2、/W3、/W4、/Wall、/wd、/we、/wo、/Wv、/Wx （警告等级）](../../build/reference/compiler-option-warning-level.md) 。

## <a name="example"></a>示例

下面的示例生成 C4439。

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```