---
title: "QueryInterface | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "接口, 可用性"
  - "接口, 指针"
  - "QueryInterface 方法"
ms.assetid: 62fce95e-aafa-4187-b50b-e6611b74c3b3
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

虽然具有对象可以表示的功能的机制它提供静态\(在实例化之前\)，从而COM结构是使用调用 [QI](http://msdn.microsoft.com/library/windows/desktop/ms682521)的 **IUnknown** 方法。  
  
 每个接口从 **IUnknown**派生，因此，每个接口具有 `QueryInterface`的实现。  无论实现，此方法查询对象的调用方需要指针接口的IID。  如果对象支持该接口，`QueryInterface` 检索指向接口，不过，同一调用 `AddRef`。  否则，它将返回 **E\_NOINTERFACE** 错误代码。  
  
 请注意必须始终遵循 [引用计数](../atl/reference-counting.md) 规则。  如果对接口指针的 **Release** 递减引用计数为零，则不应再使用该指针。  有时可能需要获取弱引用对象\(即您可能希望获取指向其接口之一，而不会递增引用计数\)，但是，通过调用 `QueryInterface` 执行此操作不可接受后跟 **Release**。  以这种方式获取的指针无效，并且不应使用。  此很容易会变得很明显，当 [\_ATL\_DEBUG\_INTERFACES](../Topic/_ATL_DEBUG_INTERFACES.md) 定义时，因此，定义此宏是一种有用的方法查找引用计数bug。  
  
## 请参阅  
 [COM 介绍](../atl/introduction-to-com.md)   
 [QueryInterface: Navigating in an Object](http://msdn.microsoft.com/library/windows/desktop/ms687230)