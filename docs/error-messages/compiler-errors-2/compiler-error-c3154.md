---
title: 编译器错误 C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: d14b921afa3888f1a9497f19bfeaa013b147b086
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50430545"
---
# <a name="compiler-error-c3154"></a>编译器错误 C3154

应、 前省略号。 非逗号分隔的省略号参数数组函数上不受支持。

未正确声明的变量自变量函数。

有关详细信息，请参阅[变量自变量列表 （...）(C + + CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>示例

下面的示例生成 C3154。

```
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```