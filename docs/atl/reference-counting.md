---
title: "Reference Counting | Microsoft Docs"
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
  - "AddRef method [C++]"
  - "AddRef method [C++], reference counting"
  - "reference counting"
  - "reference counts"
  - "引用, 计数"
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Reference Counting
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM不会自动尝试从内存中移除对象，则认为时不再使用对象。  相反，对象程序员必须移除未使用的对象。  程序员确定是否可以移除对象基于引用计数。  
  
 COM使用 **IUnknown** 方法，[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [版本](http://msdn.microsoft.com/library/windows/desktop/ms682317)，托管引用计数。对象的接口。  调用这些方法一般规则是:  
  
-   每当客户端接收接口指针，必须对 `AddRef` 接口。  
  
-   使用接口指针，每当客户端已完成，因此必须调用 **Release**。  
  
 在一个简单的实现，每 `AddRef` 调用递增，并且每 **Release** 调用减量在对象中的一个计数器变量。  在计数返回时为零，接口不再有任何用户并可以自由从内存中移除它。  
  
 reference计数还能实现，以便每对对象\(而非单个接口\)计数。  在此情况下，每 `AddRef` 和 **Release** 调用委托对对象的一个中心实现，并且，**Release** 释放整个对象，其引用计数达到零时。  
  
> [!NOTE]
>  当 `CComObject`\-使用 **new** 运算符，派生的对象构造，引用计数为0。  因此，必须在成功创建 `CComObject`后调用 `AddRef` 的是派生的对象。  
  
## 请参阅  
 [COM 介绍](../atl/introduction-to-com.md)   
 [Managing Object Lifetimes through Reference Counting](http://msdn.microsoft.com/library/windows/desktop/ms687260)