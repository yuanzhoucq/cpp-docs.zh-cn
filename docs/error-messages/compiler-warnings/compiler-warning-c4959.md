---
title: 编译器警告 C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 646347dec7bc2bac7fa73c8f754d2f9549cb2ba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473653"
---
# <a name="compiler-warning-c4959"></a>编译器警告 C4959

> 不能定义非托管的结构*类型*/clr: safe 中因为访问其成员会产生不可验证代码

## <a name="remarks"></a>备注

访问非托管类型的成员会生成无法验证的 (peverify.exe) 映像。

有关详细信息，请参阅[纯代码和可验证代码 (C + + CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。

**/Clr: safe**编译器选项在 Visual Studio 2015 中弃用并在 Visual Studio 2017 中不受支持。

此警告作为错误发出，可通过 [warning](../../preprocessor/warning.md) 杂注或 [/wd](../../build/reference/compiler-option-warning-level.md) 编译器选项禁用该警告。

## <a name="example"></a>示例

下面的示例生成 C4959：

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```