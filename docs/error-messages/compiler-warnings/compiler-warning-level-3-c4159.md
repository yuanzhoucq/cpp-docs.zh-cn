---
title: 编译器警告（等级3） C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 20d6010cb83107946c00f2f7b00cda771b2e70b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199012"
---
# <a name="compiler-warning-level-3-c4159"></a>编译器警告（等级3） C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma （pop,...）：已弹出先前推送的标识符 "*identifier*"

## <a name="remarks"></a>备注

你的源代码包含带有杂注标识符的**推送**指令，后跟不带标识符的**pop**指令。 因此，会弹出*标识符*，以后使用*标识符*可能会导致意外的行为。

## <a name="example"></a>示例

为避免出现此警告，请在**pop**指令中指定一个标识符。 例如：

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```
