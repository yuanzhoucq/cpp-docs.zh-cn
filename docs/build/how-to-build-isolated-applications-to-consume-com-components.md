---
title: "如何：生成独立应用程序以使用 COM 组件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "独立的应用程序 [C++]"
ms.assetid: 04587547-1174-44ab-bd99-1292358fba20
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 如何：生成独立应用程序以使用 COM 组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

独立应用程序是具有内置到程序中的清单的应用程序。  可以创建独立应用程序以使用 COM 组件。  
  
### 将 COM 引用添加到独立应用程序的清单中  
  
1.  打开独立应用程序的项目属性页。  
  
2.  展开**“配置属性”**节点，再展开**“清单工具”**节点。  
  
3.  选择**“独立 COM”**属性页，然后将**“组件文件名”**属性设置为希望独立应用程序使用的 COM 组件的名称。  
  
4.  单击**“确定”**。  
  
### 将清单内置于独立应用程序中  
  
1.  打开独立应用程序的项目属性页。  
  
2.  展开**“配置属性”**节点，再展开**“清单工具”**节点。  
  
3.  选择**“输入和输出”**属性页，然后将**“嵌入清单”**属性设置为**“是”**。  
  
4.  单击**“确定”**。  
  
5.  生成解决方案。  
  
## 请参阅  
 [独立应用程序](http://msdn.microsoft.com/library/aa375190)   
 [并行程序集](_win32_side_by_side_assemblies)