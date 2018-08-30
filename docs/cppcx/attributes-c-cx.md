---
title: 特性 (C + + /cli CX) |Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 491b3cabd8003664a34543d8bb7a640759bd50ee
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207400"
---
# <a name="attributes-ccx"></a>特性 (C++/CX)
属性是一种特殊的 ref 类，可以附加到 Windows 运行时类型和方法，以指定元数据创建中的某些行为的方括号中。 几个预定义属性 — 例如， [Windows::Foundation::Metadata::WebHostHidden](https://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.webhosthiddenattribute.aspx)— 通常用在 C + + /CX 代码。 此示例演示如何将特性应用于类：  
  
 [!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]  
  
## <a name="custom-attributes"></a>自定义特性  
 还可以定义自定义特性。 自定义特性必须符合这些 Windows 运行时规则：  
  
-   自定义特性只能包含公共字段。  
  
-   自定义特性字段可在将特性应用于类时初始化。  
  
-   字段可属于下列类型之一：  
  
    -   int32 (int)  
  
    -   uint32 (unsigned int)  
  
    -   bool  
  
    -   Platform::String^  
  
    -   Windows::Foundation::HResult  
  
    -   Platform::Type^  
  
    -   公共枚举类（包括用户定义的枚举）  
  
 下一个示例演示如何定义自定义特性，并在你使用它时进行初始化。  
  
 [!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]  
  
## <a name="see-also"></a>请参阅  
 [类型系统 (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Visual c + + 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)