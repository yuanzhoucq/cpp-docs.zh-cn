---
title: "接口 (ATL) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 95dce7d707cfb29c8f33f94504c26b5b24ef4c4f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="interfaces-atl"></a>接口 (ATL)
接口是在其中一个对象公开到外界其功能的方式。 在 COM 中，接口是一个表 （如 c + + vtable) 指向的对象实现的函数的指针。 表表示的接口，和它所指向的函数是该接口的方法。 对象可能会公开它选择的任意多个接口。  
  
 每个接口开始算起的基本的 COM 接口， [IUnknown](../atl/iunknown.md)。 方法**IUnknown**允许导航到其他由对象公开的接口。  
  
 此外，每个接口提供唯一的接口 ID (IID)。 这种唯一性可以轻松支持接口的版本控制。 接口的新版本是只需一个新接口，使用新的 IID。  
  
> [!NOTE]
>  预定义的标准的 COM 和 OLE 接口的 Iid。  
  
## <a name="see-also"></a>请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [COM 对象和接口](http://msdn.microsoft.com/library/windows/desktop/ms690343)

