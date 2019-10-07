---
title: 接口 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 2373351330982623ffa602fd81bec61d0bc257b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492129"
---
# <a name="interfaces-atl"></a>接口 (ATL)

接口是对象向外部公开其功能的方式。 在 COM 中, 接口是由对象实现的函数 (如C++ vtable) 的指针表。 该表表示接口, 它指向的函数是该接口的方法。 对象可以公开所选的任意数量的接口。

每个接口都基于基本 COM 接口[IUnknown](../atl/iunknown.md)。 的`IUnknown`方法允许导航到对象公开的其他接口。

此外, 为每个接口提供一个唯一的接口 ID (IID)。 这种唯一性使支持接口版本控制变得轻松。 新版本的接口只是新的接口, 具有新的 IID。

> [!NOTE]
>  标准 COM 和 OLE 接口的 Iid 是预定义的。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[COM 对象和接口](/windows/win32/com/com-objects-and-interfaces)
