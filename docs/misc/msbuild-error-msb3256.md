---
title: "MSBuild 错误 MSB3256 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3256"
ms.assetid: 809ccd0a-78cd-4bf5-83a8-2fb51815ea27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3256
**MSB3256: 未从 redist 列表读入程序集。  未能生成 TargetFramework 子集排除列表。**  
  
 未能找到可再发行项列表（redist 列表）。  
  
 若要生成程序集列表从 .NET Framework 子集排除，需要两个文件： “redist 列表”名为 FrameworkList.xml，在 .NET Framework 包含可再发行组件项目的名称，并且，“子集列表”名为 client.xml，在 .NET Framework 包含项目的名称。  由于子集定义了两个列表，因此，如果 redist 列表缺少，然后 .NET Framework 子集不能为目标。  
  
 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)]是完整的 [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] 运行库的子集。  有关 [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] 的更多信息，请参见[.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md)。  
  
### 更正此错误  
  
-   提供名为 FrameworkList.xml 的有效 redist 列表，或者以完整的 [!INCLUDE[net_v35_short](../misc/includes/net_v35_short_md.md)] 可再发行库为目标。  有关如何以完整的 [!INCLUDE[dnprdnshort](../Token/dnprdnshort_md.md)] 为目标的信息，请参见[如何：面向 .NET Framework 的某个版本](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md)。  
  
## 请参阅  
 [目标 Framework 和目标平台](../Topic/MSBuild%20Target%20Framework%20and%20Target%20Platform.md)   
 [Project 元素 \(MSBuild\)](../Topic/Project%20Element%20\(MSBuild\).md)   
 [其他资源](../Topic/Additional%20MSBuild%20Resources.md)