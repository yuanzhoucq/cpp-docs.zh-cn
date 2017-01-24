---
title: "Setting Up a Static Link to the Registrar Code (C++ Only) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "链接 [C++], to ATL Registrar code"
  - "statically linking to ATL Registrar code"
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Setting Up a Static Link to the Registrar Code (C++ Only)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+客户端可以创建静态链接到控制器的代码。  静态链接控制器的分析器添加大致5K为发布版本。  
  
 操作的最简单方式设置静态链接假定您在对象的声明中指定了 [DECLARE\_REGISTRY\_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md)。  （这是ATL使用的默认规范。）  
  
### 使用DECLARE\_REGISTRY\_RESOURCEID，创建静态链接  
  
1.  指定 [\/D](../build/reference/d-preprocessor-definitions.md)`_ATL_STATIC_REGISTRY` 代替\/D**\_ATL\_DLL**。  
  
2.  重新编译。  
  
## 请参阅  
 [注册表组件（注册器）](../atl/atl-registry-component-registrar.md)