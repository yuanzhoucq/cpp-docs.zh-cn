---
title: 编译器错误 C2660 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2660
dev_langs:
- C++
helpviewer_keywords:
- C2660
ms.assetid: 2e01a1db-4f00-4df6-a04d-cb6f70a6922b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 389e56c778a626572d0254324791af17a3108622
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042458"
---
# <a name="compiler-error-c2660"></a>编译器错误 C2660

function： 函数不采用数字参数

该函数调用的参数数目不正确。

如果您意外调用 Windows API 函数而不是相同的名称的 MFC 成员函数，则会发生 C2660。 若要解决此问题：

- 调整以符合成员函数调用的格式的函数调用。

- 使用范围解析运算符 (`::`) 以告知编译器要查找全局命名空间中的函数名称。

## <a name="example"></a>示例

下面的示例生成 C2660。

```
// C2660.cpp
void func( int, int ) {}

int main() {
   func( 1 );   // C2660 func( int ) not declared
   func( 1, 0 );   // OK
}
```

## <a name="example"></a>示例

如果尝试直接调用的托管类型的 Dispose 方法，也可能发生 C2660。 有关详细信息，请参阅[析构函数和终结器](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)。 下面的示例生成 C2660。

```
// C2660_a.cpp
// compile with: /clr
using namespace System;
using namespace System::Threading;

void CheckStatus( Object^ stateInfo ) {}

int main() {
   ManualResetEvent^ event = gcnew ManualResetEvent( false );
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );

   stateTimer->Dispose();   // C2660
   stateTimer->~Timer();   // OK
}
```

## <a name="example"></a>示例

如果派生的类隐藏了函数，将发生 C2660。

```
// C2660b.cpp
// C2660 expected
#include <stdio.h>

class f {
public:
   void bar() {
      printf_s("in f::bar\n");
    }
};

class f2 : public f {
public:
   void bar(int i){printf("in f2::bar\n");}
   // Uncomment the following line to resolve.
   // using f::bar;   // - using declaration added
   // or
   // void bar(){__super::bar();}
};

int main() {
   f2 fObject;
   fObject.bar();
}
```

## <a name="example"></a>示例

如果错误地调用索引的属性，则会发生 C2660。

```
// C2660c.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(1.9) {}
   property double MyProp[] {
      double get(int i) {
         return d;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   System::Console::WriteLine(MyX->MyProp(1));   // C2660
   System::Console::WriteLine(MyX->MyProp[1]);   // OK
}
```

## <a name="example"></a>示例

如果错误地调用索引的属性，则会发生 C2660。

```
// C2660d.cpp
// compile with: /clr
ref class A{
public:
   property int default[int,int] {
      int get(int a, int b) {
         return a + b;
      }
   }
};

int main() {
   A^ a = gcnew A;
   int x = a[3][5];   // C2660
   int x2 = a[3,5];   // OK
}
```

## <a name="example"></a>示例

如果在模板类中，定义一个新的运算符，但其中 new 运算符创建一个对象，其类型是不同于封闭类型，则会发生 C2660。

```
// C2660e.cpp
// compile with: /c
#include <malloc.h>

template <class T> class CA {
private:
    static T** line;
   void* operator new (size_t, int i) {
      return 0;
   }
   void operator delete(void* pMem, int i) {
      free(pMem);
   }

public:
   CA () { new (1) T(); }   // C2660
   // try the following line instead
   // CA () { new (1) CA<int>(); }
};

typedef CA <int> int_CA;

void AAA() {
   int_CA  list;
}
```