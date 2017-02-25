---
title: "/Zc:rvalueCast（强制实施类型转换规则） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "rvaluecast"
  - "/Zc:rvalueCast"
  - "VC.Project.VCCLCompilerTool.EnforceTypeConversionRules"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 编译器选项 (C++)"
  - "强制实施类型转换规则"
  - "rvaluecast"
  - "Zc 编译器选项 (C++)"
  - "-Zc 编译器选项 (C++)"
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /Zc:rvalueCast（强制实施类型转换规则）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定 **\/Zc:rvalueCast** 选项时，编译器将根据 C\+\+11 标准将右值引用类型正确标识为转换操作的结果。  未指定该选项时，编译器行为与 Visual Studio 2012 中的行为相同。  默认情况下，**\/Zc:rvalueCast** 处于关闭状态。  若要在使用转换时符合规范并消除错误，我们建议你使用 **\/Zc:rvalueCast**。  
  
## 语法  
  
```  
/Zc:rvalueCast[-]  
```  
  
## 备注  
 如果指定了 **\/Zc:rvalueCast**，则编译器遵循 C\+\+11 标准的 5.4 节，并只将导致非引用类型的转换表达式和导致对非函数类型的右值引用的转换表达式视为右值类型。  或者默认情况下，如果指定了 **\/Zc:rvalueCast\-**，则编译器不符合标准，并且它将所有导致右值引用的转换表达式都视为右值。  
  
 如果你将转换表达式作为参数传递到采用右值引用类型的函数，请使用 **\/Zc:rvalueCast**。  当编译器确定的转换表达式类型不正确时，该默认行为会导致编译器错误 [C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)。  此示例显示在未指定 \/Zc:rvalueCast 时正确代码中的编译器错误：  
  
```cpp  
// Test of /Zc:rvalueCast  
// compile by using:  
// cl /c /Zc:rvalueCast- make_thing.cpp  
// cl /c /Zc:rvalueCast make_thing.cpp  
  
#include <utility>  
  
template <typename T>   
struct Thing {  
   // Construct a Thing by using two rvalue reference parameters  
   Thing(T&& t1, T&& t2)  
      : thing1(t1), thing2(t2) {}  
  
   T& thing1;  
   T& thing2;  
};  
  
// Create a Thing, using move semantics if possible  
template <typename T>  
Thing<T> make_thing(T&& t1, T&& t2)  
{  
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));  
}  
  
struct Test1 {  
   long a;  
   long b;  
  
   Thing<long> test() {   
      // Use identity casts to create rvalues as arguments  
      return make_thing(static_cast<long>(a), static_cast<long>(b));   
   }  
};  
  
```  
  
 在适当情况下，默认编译器行为可能不会报告错误 C2102。  在此示例中，如果在未指定 **\/Zc:rvalueCast** 时采用了由标识转换创建的右值的地址，则编译器不会报告错误：  
  
```cpp  
int main() {  
   int a = 1;  
   int *p = &a;   // Okay, take address of lvalue   
                  // Identity cast creates rvalue from lvalue;    
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value  
}  
```  
  
 有关 Visual C\+\+ 中的一致性问题的详细信息，请参阅[非标准行为](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **C\/C\+\+** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  修改**“附加选项”**属性以包含 **\/Zc:rvalueCast**，然后选择**“确定”**。  
  
## 请参阅  
 [\/Zc（一致性）](../../build/reference/zc-conformance.md)