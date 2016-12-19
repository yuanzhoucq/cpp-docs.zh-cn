---
title: "属性映射 | Microsoft Docs"
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
  - "映射, 属性"
  - "OLE DB 提供程序, 属性"
  - "属性映射"
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 属性映射
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

除了会话、行集合和可选命令对象，每个提供程序还支持一个或多个属性。  这些属性在“OLE DB 提供程序向导”创建的头文件所包含的属性映射中定义。  每个头文件在为该文件中定义的对象定义的 OLE DB 属性组中都包含一个属性映射。  包含数据源对象的头文件也包含[数据源属性](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx)的属性映射。  Session.h 包含[会话属性](https://msdn.microsoft.com/en-us/library/ms714221.aspx)的属性映射。  行集合和命令对象驻留于一个名为 *projectname*RS.h 的头文件中。  这些属性是[行集属性](https://msdn.microsoft.com/en-us/library/ms711252.aspx)组的成员。  
  
## 请参阅  
 [OLE DB 提供程序模板体系结构](../../data/oledb/ole-db-provider-template-architecture.md)