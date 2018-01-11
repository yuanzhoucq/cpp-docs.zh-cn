---
title: "上下文相关的关键字 （c + + 组件扩展） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: internal_CPP
dev_langs: C++
helpviewer_keywords: context-sensitive keywords
ms.assetid: e33da089-f434-44e9-8cce-4668d05a8939
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1d5af53c04c6ff9ec28e7b83cd3a8f9bce8307c2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="context-sensitive-keywords--c-component-extensions"></a>上下文相关的关键字（C++ 组件扩展）
*上下文相关的关键字*是只能在特定上下文中识别的语言元素。 在特定的上下文以外，区分上下文关键字可以是用户定义的符号。  
  
## <a name="all-runtimes"></a>所有运行时  
 **备注**  
  
 下面是区上下文关键字的列表：  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [委托](../windows/delegate-cpp-component-extensions.md)  
  
-   [事件](../windows/event-cpp-component-extensions.md)  
  
-   [finally](../dotnet/finally.md)  
  
-   [for each, in](../dotnet/for-each-in.md)  
  
-   [initonly](../dotnet/initonly-cpp-cli.md)  
  
-   `internal`   
  
-   [文本](../windows/literal-cpp-component-extensions.md)  
  
-   [替代](../windows/override-cpp-component-extensions.md)  
  
-   [属性](../windows/property-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   `where`(属于[泛型](../windows/generics-cpp-component-extensions.md))  
  
 出于可读性目的，你可能想要限制区分上下文关键字作为用户定义符号的使用。  
  
## <a name="windows-runtime"></a>Windows 运行时  
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 （此功能没有特定于平台的备注。）  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例显示，在合适的上下文中，`property` 区分上下文关键字可用来定义属性和变量。  
  
```  
// context_sensitive_keywords.cpp  
// compile with: /clr  
public ref class C {  
   int MyInt;  
public:  
   C() : MyInt(99) {}  
  
   property int Property_Block {   // context-sensitive keyword  
      int get() { return MyInt; }  
   }  
};  
  
int main() {  
   int property = 0;               // variable name  
   C ^ MyC = gcnew C();  
   property = MyC->Property_Block;  
   System::Console::WriteLine(++property);  
}  
```  
  
 **输出**  
  
```Output  
100  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)