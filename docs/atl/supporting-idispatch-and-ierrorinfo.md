---
title: "支持 IDispatch 和 IErrorInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IErrorInfo"
  - "IDispatch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 中的 IDispatch 类支持"
  - "IDispatchImpl 类"
  - "ATL 中的 IErrorInfo 类支持"
  - "ISupportErrorInfoImpl 方法"
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 支持 IDispatch 和 IErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您在对象可以使用模板选件类 [IDispatchImpl](../atl/reference/idispatchimpl-class.md) 提供所有双重接口的 `IDispatch Interface` 部分的默认实现。  
  
 如果您的对象使用 `IErrorInfo` 接口报告错误返回给客户端，则对象必须支持 `ISupportErrorInfo Interface` 接口。  模板选件类 [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) 提供了一种简单的方法实现此目的，如果只有在对象生成错误的单个接口中。  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../atl/fundamentals-of-atl-com-objects.md)