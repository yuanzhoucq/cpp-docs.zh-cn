---
title: "MSBuild 错误 MSB3115 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.InvalidEntryPoint"
helpviewer_keywords: 
  - "MSB3115"
ms.assetid: 7d9d4156-fd6a-455a-8a3d-b191485f1294
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild 错误 MSB3115
**MSB3115: 文件“\<file\>”不是有效的入口点。**  
  
 当清单指定了无效的入口点时，便会产生此错误。  
  
### 更正此错误  
  
-   请确保在清单中指定了有效的入口点。  对于应用程序清单，有效的入口点是一个 .exe 文件。  对于部署清单，有效的入口点是一个应用程序清单。