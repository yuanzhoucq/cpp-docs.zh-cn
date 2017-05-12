---
title: "模板 ref 类 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# 模板 ref 类 (C++/CX)
C\+\+ 模板没有发布到元数据，因此你的程序中不能具有公共或受保护的可访问性。 当然，你可在程序内部使用标准 C\+\+ 模板。 此外，你可将私有 ref 类定义为模板，并可将显式专用模板 ref 类声明为公共 ref 类中的私有成员。  
  
## 创作 ref 类模板  
 下面的示例演示如何将私有 ref 类声明为模板，如何声明标准 C\+\+ 模板，以及如何将二者同时声明为公共 ref 类中的成员。 请注意，标准 C\+\+ 模板可通过 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]类型进行专用化，此示例中为 Platform::String^。  
  
 [!code-cpp[cx_templates#01](../snippets/cpp/VS_Snippets_Misc/cx_templates/cpp/class1.h#01)]  
  
## 请参阅  
 [类型系统 \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Visual C\+\+ 语言参考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空间参考](../cppcx/namespaces-reference-c-cx.md)