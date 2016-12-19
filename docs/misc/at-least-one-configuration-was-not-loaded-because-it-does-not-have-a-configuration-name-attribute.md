---
title: "At least one configuration was not loaded because it does not have a configuration name attribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.projfile_nameless_config"
ms.assetid: 711f7253-308b-44e0-b8bc-ca5c16536a2c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# At least one configuration was not loaded because it does not have a configuration name attribute
.csproj 或 .vbproj 文件中的每个 `<Config>` 节都必须具有 Name 特性，该特性定义该配置的唯一名称。  该诊断指示缺少 Name 特性。  如果“配置”上缺少 Name 特性，则不会将该配置加载到项目中。  
  
 此错误很可能由手动编辑项目文件引起。  
  
 **更正此错误**  
  
-   在项目文件中紧接在 `<Config>` 行之后插入配置名称。  
  
    ```  
    Name = "someconfigname"  
    ```  
  
     典型的配置名称是 `Debug` 或 `Release`。  
  
## 请参阅  
 [项目文件](../ide/project-files.md)   
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-cn/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)