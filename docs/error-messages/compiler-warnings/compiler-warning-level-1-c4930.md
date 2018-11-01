---
title: 编译器警告（等级 1）C4930
ms.date: 11/04/2016
f1_keywords:
- C4930
helpviewer_keywords:
- C4930
ms.assetid: 89a206c9-c536-4186-8e81-1cde3e7f4f5b
ms.openlocfilehash: 15cd1ed61c747e2c9168b9fc0fee03dca8403a24
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560168"
---
# <a name="compiler-warning-level-1-c4930"></a>编译器警告（等级 1）C4930

原型： 未调用原型函数 （是否有意用变量定义？）

编译器检测到未使用的函数原型。 如果作为变量声明有意将该原型，删除左/右括号。

下面的示例生成 C4930:

```
// C4930.cpp
// compile with: /W1
class Lock {
public:
   int i;
};

void f() {
   Lock theLock();   // C4930
   // try the following line instead
   // Lock theLock;
}

int main() {
}
```

当编译器无法区分函数原型声明和函数调用时，也会出现 C4930。

下面的示例生成 C4930:

```
// C4930b.cpp
// compile with: /EHsc /W1

class BooleanException
{
   bool _result;

public:
   BooleanException(bool result)
      : _result(result)
   {
   }

   bool GetResult() const
   {
      return _result;
   }
};

template<class T = BooleanException>
class IfFailedThrow
{
public:
   IfFailedThrow(bool result)
   {
      if (!result)
      {
         throw T(result);
      }
   }
};

class MyClass
{
public:
   bool MyFunc()
   {
      try
      {
         IfFailedThrow<>(MyMethod()); // C4930

         // try one of the following lines instead
         // IfFailedThrow<> ift(MyMethod());
         // IfFailedThrow<>(this->MyMethod());
         // IfFailedThrow<>((*this).MyMethod());

         return true;
      }
      catch (BooleanException e)
      {
         return e.GetResult();
      }
   }

private:
   bool MyMethod()
   {
      return true;
   }
};

int main()
{
   MyClass myClass;
   myClass.MyFunc();
}
```

在上面的示例中，采用零个参数的方法的结果是作为参数传递给构造函数的未命名的本地类变量。 在调用可以通过命名本地变量或前缀与相应的指针到成员运算符以及对象实例的方法调用来消除歧义。