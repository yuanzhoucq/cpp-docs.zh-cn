---
title: "编译器警告（等级 2）C4412 | Microsoft Docs"
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
  - "C4412"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4412"
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4412
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 函数签名包含类型 'type'；在纯代码与混合代码或本机代码之间传递 C\+\+ 对象是不安全的。  
  
 编译器已检测到可能导致运行时错误的潜在的不安全情况：将从某个 **\/clr:pure** compiland 中调用已通过 dllimport 导入的函数，该函数签名包含不安全的类型。（译者注：compiland 为基本的编译或转换单位。一个项目通常包括若干 compiland（如 .c 和 .cpp 文件），系统编译 compiland 以产生对应的对象文件。）  如果类型包含成员函数或具有数据成员（它们为不安全类型或为到不安全类型的间接寻址），则该类型不安全。  
  
 不安全的原因在于纯代码与本机代码（或混合本机代码与托管代码）之间的默认调用约定存在差异。  将函数导入（通过 `dllimport`）**\/clr:pure** compiland 中时，请确保签名中每种类型的声明都与导出函数的 compiland 中的声明相同（应特别注意隐式调用约定中的差异）。  
  
 虚拟成员函数特别容易产生意外结果。但是即便如此，也应测试非虚函数，以确保获得正确的结果。  如果确保将获得正确结果，则可以忽略此警告。  
  
 有关 **\/clr:pure** 的更多信息，请参见 [如何：迁移到 \/clr:pure](../../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)。  
  
 默认情况下，C4412 处于关闭状态。  有关更多信息，请参见 [默认情况下处于关闭状态的编译器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 和 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)。  
  
 若要解除此警告，请从该类型中移除所有函数。  
  
## 示例  
 下面的示例生成 C4412。  
  
```  
// C4412.cpp  
// compile with: /c /W2 /clr:pure  
#pragma warning (default : 4412)  
  
struct Unsafe {  
   virtual void __cdecl Test();  
};  
  
struct Safe {  
   int i;  
};  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   Unsafe *pUnsafe = func();   // C4412  
   // pUnsafe->Test();  
  
   Safe *pSafe = func2();   // OK  
}  
```  
  
## 示例  
 下面的示例是用于声明两个类型的头文件。  `Unsafe` 类型有成员函数，因此是不安全的。  
  
```  
// C4412.h  
struct Unsafe {  
   // will be __clrcall if #included in pure compilation  
   // defaults to __cdecl in native or mixed mode compilation  
   virtual void Test(int * pi);  
  
   // try the following line instead  
   // virtual void __cdecl Test(int * pi);  
};  
  
struct Safe {  
   int i;  
};  
```  
  
## 示例  
 此示例使用头文件中定义的类型导出函数。  
  
```  
// C4412_2.cpp  
// compile with: /LD  
#include "C4412.h"  
  
void Unsafe::Test(int * pi) {  
   *pi++;  
}  
  
__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }  
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }  
```  
  
## 示例  
 **\/clr:pure** 编译中的默认调用约定不同于本机编译中的对应约定。包括 C4412.h 时，`Test` 将默认为 `__clrcall`。  如果编译并运行此程序（不使用 **\/c**），该程序将引发异常。  
  
 下面的示例生成 C4412。  
  
```  
// C4412_3.cpp  
// compile with: /W2 /clr:pure /c /link C4412_2.lib  
#pragma warning (default : 4412)  
#include "C4412.h"  
  
__declspec(dllimport) Unsafe * __cdecl func();  
__declspec(dllimport) Safe * __cdecl func2();  
  
int main() {  
   int n = 7;  
   Unsafe *pUnsafe = func();   // C4412  
   pUnsafe->Test(&n);  
  
   Safe *pSafe = func2();   // OK  
}  
```