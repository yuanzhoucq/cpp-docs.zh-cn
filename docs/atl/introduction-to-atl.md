---
title: ATL 简介
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
ms.openlocfilehash: 5eba816bc87eeebea2c41489a5d15c48645739e8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492106"
---
# <a name="introduction-to-atl"></a>ATL 简介

ATL 是活动模板库, 它是一组基于C++模板的类, 您可以使用这些类轻松地创建小型的快速组件对象模型 (COM) 对象。 它有对关键 COM 功能的特殊支持, 包括: [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)、 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)、 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)和`IDispatch`、双重接口的常用实现、标准 COM 枚举器接口、连接点、脱离接口和 ActiveX 控件。

ATL 代码可用于创建单线程对象、单元模型对象、自由线程模型对象或自由线程模型对象和单元模型对象。

本部分中涵盖的主题包括:

- [模板库](../atl/using-a-template-library.md)与标准库的不同之处。

- [可以和不能通过 ATL 执行的操作](../atl/scope-of-atl.md)。

- [用于在 ATL 和 MFC 之间进行选择的建议](../atl/recommendations-for-choosing-between-atl-and-mfc.md)。

## <a name="see-also"></a>请参阅

[COM 和 ATL 介绍](../atl/introduction-to-com-and-atl.md)
