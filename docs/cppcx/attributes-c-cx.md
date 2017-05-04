---
title: "特性 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# 特性 (C++/CX)
特性是一类特殊的 ref 类，可在方括号中将其附加在 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型和方法之前，以指定元数据创建中的某些行为。 几个预定义属性 — 例如，[Windows::Foundation::Metadata::WebHostHidden](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx) — 中常用 [!INCLUDE[cppwrt_short](../cppcx/includes/cppwrt-short-md.md)] 代码。 此示例演示如何将特性应用于类：  
  
 [!code-cpp[cx_attributes#01](../snippets/cpp/VS_Snippets_Misc/cx_attributes/cpp/class1.h#01)]  
  
## 自定义特性  
 还可以定义自定义特性。 自定义特性必须遵循这些 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]规则：  
  
-   自定义特性只能包含公共字段。  
  
-   自定义特性字段可在将特性应用于类时初始化。  
  
-   字段可属于下列类型之一：  
  
    -   int32 \(int\)  
  
    -   uint32 \(unsigned int\)  
  
    -   bool  
  
    -   Platform::String^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::Type^  
  
    -   公共枚举类（包括用户定义的枚举）  
  
 下一个示例演示如何定义自定义特性，并在你使用它时进行初始化。  
  
 [!code-cpp[cx_attributes#02](../snippets/cpp/VS_Snippets_Misc/cx_attributes/cpp/class1.h#02)]  
  
## 请参阅  
 [类型系统 \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)