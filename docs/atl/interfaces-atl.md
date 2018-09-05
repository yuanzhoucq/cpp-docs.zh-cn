---
title: 接口 (ATL) |Microsoft Docs
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
ms.openlocfilehash: 04f77981bd922f73c99102c444a7c95f7240adbc
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764615"
---
# <a name="interfaces-atl"></a>接口 (ATL)

接口是一个对象用于公开到外界其功能的方法。 在 COM 中，接口是由对象实现的函数的指针 （如 c + + vtable) 的表。 表表示的接口，和它所指向的函数是该接口的方法。 对象可以公开它选择任意数目的接口。

在基本的 COM 接口上基于每个接口[IUnknown](../atl/iunknown.md)。 方法`IUnknown`允许导航到由对象公开其他接口。

此外，每个接口有一个唯一的接口 ID (IID)。 此唯一性轻松支持接口的版本控制。 接口的新版本是只是一个新接口，使用新的 IID。

> [!NOTE]
>  预定义的标准的 COM 和 OLE 接口的 Iid。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)   
[COM 对象和接口](/windows/desktop/com/com-objects-and-interfaces)

