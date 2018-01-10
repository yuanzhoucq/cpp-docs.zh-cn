---
title: "-Zc: rvalueCast （强制实施类型转换规则） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f4b888dde70708ee10b2d8000ff6380709dc870
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast（强制实施类型转换规则）
当**/zc: rvaluecast**指定选项，编译器会正确标识根据 C + + 11 标准转换运算的结果为右值引用类型。 未指定该选项时，编译器行为与 Visual Studio 2012 中的行为相同。 默认情况下， **/zc: rvaluecast**处于关闭状态。 有关一致性以及消除使用转换中的错误，我们建议你使用**/zc: rvaluecast**。  
  
## <a name="syntax"></a>语法  
  
```  
/Zc:rvalueCast[-]  
```  
  
## <a name="remarks"></a>备注  
 如果**/zc: rvaluecast**指定，则编译器遵循 C + + 11 标准的 5.4 节，并将仅强制转换表达式，导致非引用类型的转换导致对非函数类型的右值引用的表达式作为右值类型。 默认情况下，或者如果**/Zc:rvalueCast-**指定，编译器不符合标准，并将所有导致右值引用视为右值的强制转换表达式。  
  
 使用**/zc: rvaluecast**如果强制转换表达式作为自变量传递给采用右值引用类型的函数。 默认行为将导致编译器错误[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)编译器错误地确定强制转换表达式的类型。 此示例显示在未指定 /Zc:rvalueCast 时正确代码中的编译器错误：  
  
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
  
 在适当情况下，默认编译器行为可能不会报告错误 C2102。 在此示例中，编译器不报告错误时，采用了由标识转换创建的右值的地址如果**/zc: rvaluecast**未指定：  
  
```cpp  
int main() {  
   int a = 1;  
   int *p = &a;   // Okay, take address of lvalue   
                  // Identity cast creates rvalue from lvalue;    
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value  
}  
```  
  
 有关 Visual C++ 中一致性问题的详细信息，请参阅 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的“属性页”  对话框。 有关详细信息，请参阅[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择**C/c + +**文件夹。  
  
3.  选择**命令行**属性页。  
  
4.  修改**其他选项**属性以包含**/zc: rvaluecast** ，然后选择**确定**。  
  
## <a name="see-also"></a>请参阅  
 [/Zc （一致性）](../../build/reference/zc-conformance.md)