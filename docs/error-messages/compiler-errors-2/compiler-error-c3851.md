---
title: 编译器错误 C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165571"
---
# <a name="compiler-error-c3851"></a>编译器错误 C3851

> "*char*"：通用字符名称不能指定基本字符集中的字符

## <a name="remarks"></a>备注

在编译为 C++ 的代码中，无法使用在字符串或字符文本之外表示基本源字符集中的字符的通用字符名称。 有关详细信息，请参阅 [Character Sets](../../cpp/character-sets.md)。 在编译为 C 的代码中，不能将通用字符名称用于包含 0x20-0x7f 范围内的字符，但0x24 （' $ '）、0x40 （'\@'）或0x60 （'\`'）除外。

## <a name="example"></a>示例

下面的示例生成 C3851，并显示如何修复此问题：

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
