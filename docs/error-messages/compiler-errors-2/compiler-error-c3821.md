---
title: 编译器错误 C3821
ms.date: 11/04/2016
f1_keywords:
- C3821
helpviewer_keywords:
- C3821
ms.assetid: 2b327c7a-5faf-443c-ae82-944fae25b4df
ms.openlocfilehash: 248431afb25aa4b9480818f76388f6ad56d8e006
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384226"
---
# <a name="compiler-error-c3821"></a>编译器错误 C3821

function： 托管的类型或函数不能使用非托管函数

使用内联程序集的函数或[setjmp](../../c-runtime-library/reference/setjmp.md)不能包含值类型或托管的类。 若要修复此错误，删除内联程序集和`setjmp`或删除托管的对象。

如果你尝试在 vararg 函数中使用自动存储，也可能发生 C3821。  有关详细信息，请参阅[变量自变量列表 （...）(C++/CLI)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)并[C++用于引用类型堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

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
