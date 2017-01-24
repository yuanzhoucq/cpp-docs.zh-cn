---
title: "% (跟踪引用) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "% 跟踪引用 [C++]"
  - "跟踪引用"
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
caps.latest.revision: 31
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# % (跟踪引用)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

“跟踪引用”\(`%`\) 的行为与普通 C\+\+ 引用 \(`&`\) 相似，区别在于，将对象指定给跟踪引用时，对象的引用计数会递增。  
  
## 所有平台  
 跟踪引用具有下列特征：  
  
-   将对象分配给跟踪引用会导致对象的引用计数递增。  
  
-   本机引用 \(&\) 是您取消引用 \* 时的结果。  跟踪引用 \(%\) 是您取消引用 ^ 时的结果。  只要有指向对象的 %，该对象就会一直保留在内存中。  
  
-   点 \(`.`\) 成员访问运算符用于访问对象的成员。  
  
-   跟踪引用对值类型和句柄 \(`String^`\) 有效。  
  
-   不能为跟踪引用赋 null 值或赋 `nullptr` 值。  根据需要，可以将一个跟踪引用重新分配给另一个有效对象，没有次数限制。  
  
-   跟踪引用不能用作一元获取地址运算符。  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 跟踪引用的行为与标准 C\+\+ 引用相似，区别在于，% 是对引用计数的引用。  下面的代码段演示如何在 % 和 ^ 类型之间转换：  
  
```  
Foo^ spFoo = ref new Foo();  
Foo% srFoo = *spFoo;  
Foo^ spFoo2 = %srFoo;  
```  
  
 下面的示例演示如何将 ^ 传递到采用了 % 的函数。  
  
```  
  
ref class Foo sealed {};  
  
    // internal or private  
    void UseFooHelper(Foo% f)  
    {  
        auto x = %f;  
    }  
  
    // public method on ABI boundary  
    void UseFoo(Foo^ f)  
    {  
        if (f != nullptr) { UseFooHelper(*f); }  
    }  
  
```  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 在 C\+\+\/CLI 中，当你绑定到垃圾回收堆上 CLR 类型的对象时，可以使用句柄的跟踪引用。  
  
 在 CLR 中，只要垃圾回收器移动引用的对象，跟踪引用变量的值就会自动更新。  
  
 只能在堆栈上声明跟踪引用。  跟踪引用不能成为类的成员。  
  
 不可能对垃圾回收堆上的对象进行本机 C\+\+ 引用。  
  
 有关 C\+\+\/CLI 中跟踪引用的详细信息，请参阅：  
  
-   [如何：在 C\+\+\/CLI 中使用跟踪引用](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)  
  
-   [如何：使用跟踪引用和值类型](../misc/how-to-use-tracking-references-and-value-types.md)  
  
-   [如何：使用跟踪引用和内部指针](../misc/how-to-use-tracking-references-and-interior-pointers.md)  
  
-   [如何：编写采用本机、值或引用参数的模板函数](../misc/how-to-write-template-functions-that-take-native-value-or-reference-parameters.md)  
  
### 示例  
 **示例**  
  
 下面针对 C\+\+\/CLI 的示例演示如何搭配使用跟踪引用与本机和托管类型。  
  
```  
// tracking_reference_1.cpp  
// compile with: /clr  
ref class MyClass {  
public:  
   int i;  
};  
  
value struct MyStruct {  
   int k;  
};  
  
int main() {  
   MyClass ^ x = ref new MyClass;  
   MyClass ^% y = x;   // tracking reference handle to reference object   
  
   int %ti = x->i;   // tracking reference to member of reference type  
  
   int j = 0;  
   int %tj = j;   // tracking reference to object on the stack  
  
   int * pi = new int[2];  
   int % ti2 = pi[0];   // tracking reference to object on native heap  
  
   int *% tpi = pi;   // tracking reference to native pointer  
  
   MyStruct ^ x2 = ref new MyStruct;  
   MyStruct ^% y2 = x2;   // tracking reference to value object  
  
   MyStruct z;  
   int %tk = z.k;   // tracking reference to member of value type  
  
   delete[] pi;  
}  
  
```  
  
 **示例**  
  
 下面针对 C\+\+\/CLI 的示例演示如何将跟踪引用绑定到数组。  
  
```  
// tracking_reference_2.cpp  
// compile with: /clr  
using namespace System;  
  
int main() {  
   array<int> ^ a = ref new array< Int32 >(5);  
   a[0] = 21;  
   Console::WriteLine(a[0]);  
   array<int> ^% arr = a;  
   arr[0] = 222;  
   Console::WriteLine(a[0]);  
}  
```  
  
 **输出**  
  
  **21**  
 **222**