---
title: "编译器错误 C3767 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3767"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3767"
ms.assetid: 5247cdcd-639c-4527-bd37-37e74c4e8fab
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3767
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”候选函数不可访问  
  
 在类中定义的友元函数不应被视为在全局命名空间范围中定义和声明了它。  但是，可以通过依赖于参数的查找找到它。  
  
 C3767 还可能由重大的更改引起：现在，默认情况下在 **\/clr** 编译中本机类型为私有的；有关详细信息，请参阅 [类型可见性](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) 。  
  
 下面的示例生成 C3767：  
  
```  
// C3767a.cpp  
// compile with: /clr  
using namespace System;  
public delegate void TestDel();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;  
};  
  
public ref class MyClass2 : public MyClass {  
public:  
   void Test() {  
      MyClass^ patient = gcnew MyClass;  
      patient->MyClass_Event();  
    }  
};  
  
int main() {  
   MyClass^ x = gcnew MyClass;  
   x->MyClass_Event();   // C3767  
  
   // OK  
   MyClass2^ y = gcnew MyClass2();  
   y->Test();  
};  
```  
  
 下面的示例生成 C3767：  
  
```  
// C3767b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__delegate void TestDel();  
  
public __gc class MyClass {  
public:  
   static __event TestDel * MyClass_Event;  
};  
  
public __gc class MyClass2 : public MyClass {  
public:  
   void Test() {  
      MyClass* patient = new MyClass;  
      patient->MyClass_Event();  
    }  
};  
  
int main() {  
   MyClass* x = new MyClass;  
   x->MyClass_Event();   // C3767  
  
   // OK  
   MyClass2 * y = new MyClass2();  
   y->Test();  
};  
```  
  
 下面的示例生成 C3767：  
  
```  
// C3767c.cpp  
// compile with: /clr /c  
  
ref class Base  {  
protected:  
   void Method() {  
      System::Console::WriteLine("protected");  
   }  
};  
  
ref class Der : public Base {  
   void Method() {  
      ((Base^)this)->Method();   // C3767  
      // try the following line instead  
      // Base::Method();  
   }  
};  
```  
  
 下面的示例生成 C3767：  
  
```  
// C3767d.cpp  
// compile with: /clr:oldSyntax /c  
  
__gc class Base {  
protected:  
   void Method() {  
      System::Console::WriteLine("protected");  
   }  
};  
  
__gc class Der : public Base {  
   void Method() {  
      ((Base*)this)->Method();   // C3767  
      // try the following line instead  
      // Base::Method();  
   }  
};  
```  
  
 在 Visual C\+\+ .NET 2002 中，编译器更改了查找符号的方式。  在某些情况下，它会在指定的命名空间中自动查找符号。  现在，它将使用依赖于参数的查找。  
  
 下面的示例生成 C3767：  
  
```  
// C3767e.cpp  
namespace N {  
   class C {  
      friend void FriendFunc() {}  
      friend void AnotherFriendFunc(C* c) {}  
   };  
}  
  
int main() {  
   using namespace N;  
   FriendFunc();   // C3767 error  
   C* pC = new C();  
   AnotherFriendFunc(pC);   // found via argument-dependent lookup  
}  
```  
  
 对于 Visual C\+\+ .NET 2003 和 Visual C\+\+ .NET 2002 中有效的代码，在类范围中声明友元函数并在命名空间范围中定义它：  
  
```  
// C3767f.cpp  
class MyClass {  
   int m_private;  
   friend void func();  
};  
  
void func() {  
   MyClass s;  
   s.m_private = 0;  
}  
  
int main() {  
   func();  
}  
```