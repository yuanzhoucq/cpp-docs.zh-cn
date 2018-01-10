---
title: "支持 IDispatch 和 IErrorInfo |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorInfo
- IDispatch
dev_langs: C++
helpviewer_keywords:
- ISupportErrorInfoImpl method
- IErrorInfo class suppor in ATL
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 7db2220f-319d-4ce9-9382-d340019f14f7
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f39db3e844df884e8e95352bed2a078b01beede8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="supporting-idispatch-and-ierrorinfo"></a>支持 IDispatch 和 IErrorInfo
你可以使用此模板类[IDispatchImpl](../atl/reference/idispatchimpl-class.md)提供的默认实现`IDispatch Interface`上你的对象的任何双重接口的一部分。  
  
 如果你的对象使用`IErrorInfo`接口来报告错误返回到客户端，则你的对象必须支持`ISupportErrorInfo Interface`接口。 此模板类[ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md)可以轻松地实现这一如果你只有单个接口生成你的对象上的错误。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 对象基础知识](../atl/fundamentals-of-atl-com-objects.md)

