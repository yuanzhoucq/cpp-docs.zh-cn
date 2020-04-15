---
title: 封送
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319351"
---
# <a name="marshaling"></a>封送

COM 封送技术允许在一个进程中由对象公开的接口在另一个进程中使用。 在封送中，COM 提供代码（或使用接口实现器提供的代码），既将方法的参数打包成一种可以跨进程移动的格式（以及跨线移动到其他计算机上运行的进程），又在另一端解压缩这些参数。 同样，COM 必须在从呼叫返回时执行这些相同的步骤。

> [!NOTE]
> 当对象提供的接口与对象在同一进程中使用时，通常不需要封送。 但是，线程之间可能需要封送。

## <a name="see-also"></a>另请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[封送详细信息](/windows/win32/com/marshaling-details)
