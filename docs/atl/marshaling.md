---
title: "Marshaling | Microsoft Docs"
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
  - "COM 接口, 封送处理"
  - "封送处理"
  - "封送处理, COM 互操作"
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Marshaling
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM技术将允许在一个中对象公开的接口处理用于其他进程。  在封送处理，COM提供代码\(或接口实现者提供的使用代码\)两个打包方法的参数到可移动处理的格式\(以及，该连接进程之间运行在其他计算机\)和打开这些参数在另一端。  同样，COM必须在返回的这些步骤从调用。  
  
> [!NOTE]
>  对象时，提供的接口用于同一进程作为对象时，让通常不是必需的。  但是，具有可能需要的线程之间。  
  
## 请参阅  
 [COM 介绍](../atl/introduction-to-com.md)   
 [Marshaling Details](http://msdn.microsoft.com/library/windows/desktop/ms692621)