---
title: "__identifier (c + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __identifier
- __identifier_cpp
dev_langs:
- C++
helpviewer_keywords:
- __identifier keyword [C++]
ms.assetid: 348428af-afa7-4ff3-b571-acf874301cf2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d68d21fc9436bff0e39fa474b97ec54138e15b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="identifier-ccli"></a>__identifier (C++/CLI)
可以用作标识符的 Visual c + + 关键字的使用。  
  
## <a name="all-platforms"></a>所有平台  
**语法**  
  
```  
__identifier(  
Visual_C++_keyword  
)  
  
```  
  
**备注**  
  
利用`__identifier`允许使用，但强烈建议不要这样做作为一种样式不是关键字的标识符的关键字。  
  
## <a name="windows-runtime"></a>Windows 运行时  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/ZW**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 在下面的示例中，类名为`template`是在 C# 中创建和分布式为 DLL。 使用 Visual c + + 程序中`template`类，`__identifier`关键字隐藏这一事实，`template`是标准 c + + 关键字。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /ZW  
#using <identifier_template.dll>  
int main() {  
   __identifier(template)^ pTemplate = ref new __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 **备注**  
  
 `__identifier`关键字是有效，且**/clr**编译器选项。  
  
### <a name="requirements"></a>惠?  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 在下面的示例中，类名为`template`是在 C# 中创建和分布式为 DLL。 使用 Visual c + + 程序中`template`类，`__identifier`关键字隐藏这一事实，`template`是标准 c + + 关键字。  
  
```  
// identifier_template.cs  
// compile with: /target:library  
public class template {  
   public void Run() { }  
}  
```  
  
```  
// keyword__identifier.cpp  
// compile with: /clr  
#using <identifier_template.dll>  
  
int main() {  
   __identifier(template) ^pTemplate = gcnew __identifier(template)();  
   pTemplate->Run();  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)   
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)