---
title: 封送处理
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 0661a4cdde0a3a875cf27221e884f6c65b9fea55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262380"
---
# <a name="marshaling"></a>封送处理

封送处理的 COM 方法允许在一个进程可以在另一个过程中使用某个对象公开的接口。 在封送处理，COM 提供了代码 （或使用提供的接口实现器代码） 打包到跨进程 （以及在网络上其他计算机运行的进程） 可以移动的格式的方法的参数，并将这些参数解压缩在另一端。 同样，COM 必须执行上述相同步骤，在从调用返回。

> [!NOTE]
>  封送处理时通常不需要与对象相同的进程中正在使用提供的对象的接口。 但是，封送处理可能需要在线程之间。

## <a name="see-also"></a>请参阅

[COM 简介](../atl/introduction-to-com.md)<br/>
[封送处理的详细信息](/windows/desktop/com/marshaling-details)
