---
title: 接口 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0db5a79f187cb0fe320bf67aace751a5d4c537d3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
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

