---
title: 接口 (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- COM interfaces
- interfaces, COM
ms.assetid: de6c8b12-6230-4fdc-af66-a28b91d5ee55
ms.openlocfilehash: 56d5a010bc28257dce181ee33e0ddf74655ccd3c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319389"
---
# <a name="interfaces-atl"></a>接口 (ATL)

接口是对象向外部世界公开其功能的方式。 在 COM 中，接口是指向对象实现的函数的指针表（如C++可 vtable）。 表表示接口，它指向的函数是该接口的方法。 对象可以公开任意选择的接口数。

每个接口都基于基本的COM接口[，I未知。](../atl/iunknown.md) `IUnknown`允许导航到对象公开的其他接口的方法。

此外，每个接口都被授予一个唯一的接口 ID （IID）。 这种唯一性使得支持接口版本控制变得容易。 接口的新版本只是一个新的接口，带有新的 IID。

> [!NOTE]
> 预定义了标准 COM 和 OLE 接口的 IID。

## <a name="see-also"></a>另请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[COM 对象和接口](/windows/win32/com/com-objects-and-interfaces)
