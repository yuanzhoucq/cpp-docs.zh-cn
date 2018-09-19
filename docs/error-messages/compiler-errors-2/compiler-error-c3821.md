---
title: 编译器错误 C3821 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3821
dev_langs:
- C++
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e1f9a0bbb8eaae6b316b3d00e4201b2b64222ac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023028"
---
# <a name="compiler-error-c3821"></a>编译器错误 C3821

function： 托管的类型或函数不能使用非托管函数

使用内联程序集的函数或[setjmp](../../c-runtime-library/reference/setjmp.md)不能包含值类型或托管的类。 若要修复此错误，删除内联程序集和`setjmp`或删除托管的对象。

如果你尝试在 vararg 函数中使用自动存储，也可能发生 C3821。  有关详细信息，请参阅[变量自变量列表 （...）(C + + CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)并[引用类型的 c + + 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>示例

下面的示例生成 C3821。

```
// C3821a.cpp
// compile with: /clr /c
public ref struct R {};
void test1(...) {
   R r;   // C3821
}
```

## <a name="example"></a>示例

下面的示例生成 C3821。

```
// C3821b.cpp
// compile with: /clr
// processor: /x86
ref class A {
   public:
   int i;
};

int main() {
   // cannot use managed classes in this function
   A ^a;

   __asm {
      nop
   }
} // C3821
```
