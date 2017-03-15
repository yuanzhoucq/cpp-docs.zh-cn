---
title: "如何：生成免注册 COM 组件 | Microsoft Docs"
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
  - "COM 组件, 免注册"
ms.assetid: 7e585d6a-0314-45b2-8f1b-cae9ac4df037
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 如何：生成免注册 COM 组件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

免注册 COM 组件是将清单内置于 DLL 中的 COM 组件。  
  
### 将清单内置于 COM 组件中  
  
1.  打开 COM 组件的项目属性页。  
  
2.  展开**“配置属性”**节点，再展开**“清单工具”**节点。  
  
3.  选择**“输入和输出”**属性页，然后将**“嵌入清单”**属性设置为**“是”**。  
  
4.  单击**“确定”**。  
  
5.  生成解决方案。  
  
## 请参阅  
 [独立应用程序](http://msdn.microsoft.com/library/aa375190)   
 [并行程序集](_win32_side_by_side_assemblies)   
 [如何：生成独立应用程序以使用 COM 组件](../build/how-to-build-isolated-applications-to-consume-com-components.md)