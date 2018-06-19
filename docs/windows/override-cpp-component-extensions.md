---
title: 重写 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override keyword [C++]
- override keyword [C++]
ms.assetid: 34d19257-1686-4fcd-96f5-af07c70ba914
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6818256aafc64702e5423a5560c251e6d46750fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878874"
---
# <a name="override--c-component-extensions"></a>重写（C++ 组件扩展）
`override` 区分上下文的关键字表示类型成员重写基类或基接口成员。  
  
## <a name="remarks"></a>备注  
 `override`编译的本机目标 （默认编译器选项） 时，关键字是有效 Windows 运行时目标 (**/ZW**编译器选项)，或公共语言运行时目标 (**/clr**编译器选项）。  
  
 有关重写说明符的详细信息，请参阅[重写说明符](../cpp/override-specifier.md)和[重写说明符和本机编译](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)。  
  
 有关上下文相关关键字的详细信息，请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)。  
  
## <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示`override`还可在本机编译中。  
  
```cpp#  
// override_keyword_1.cpp  
// compile with: /c  
struct I1 {  
   virtual void f();  
};  
  
struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **示例**  
  
 下面的代码示例演示`override`可以在 Windows 运行时编译中使用。  
  
```cpp#  
// override_keyword_2.cpp  
// compile with: /ZW /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **要求**  
  
 编译器选项： **/ZW**  
  
 **示例**  
  
 下面的代码示例演示`override`可用在公共语言运行时编译。  
  
```cpp#  
// override_keyword_3.cpp  
// compile with: /clr /c  
ref struct I1 {  
   virtual void f();  
};  
  
ref struct X : public I1 {  
   virtual void f() override {}  
};  
```  
  
 **要求**  
  
 编译器选项： **/clr**  
  
## <a name="see-also"></a>请参阅  
 [重写说明符](../cpp/override-specifier.md)   
 [重写说明符](../windows/override-specifiers-cpp-component-extensions.md)