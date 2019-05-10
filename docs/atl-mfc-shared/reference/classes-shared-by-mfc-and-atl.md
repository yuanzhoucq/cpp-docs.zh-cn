---
title: 由 MFC 和 ATL 共享的类
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: 5376a87aac2b82615cd48f80e0e95208b8132bf0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235141"
---
# <a name="classes-shared-by-mfc-and-atl"></a>由 MFC 和 ATL 共享的类

下表列出了 MFC 和 atl。 之间共享的类

|类|描述|标头文件|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|提供用于管理与文件相关联的日期和时间值的方法。|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|提供用于管理相对日期和时间值与文件关联的方法。|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|表示具有固定的字符缓冲区的字符串对象。|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供了增强的位图支持，包括加载和保存 JPEG、 GIF、 BMP、 和可移植网络图形 (PNG) 格式图像的能力。|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|封装 OLE 自动化中使用的日期数据类型。|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|表示相对时间，时间跨度。|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|类似于 Windows 的类[点](/windows/desktop/api/windef/ns-windef-tagpoint)结构，它还包括成员函数以操作`CPoint`和`POINT`结构。|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|类似于 Windows 的类[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构，它还包括成员函数以操作`CRect`对象和 Windows`RECT`结构。|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|表示`CSimpleStringT`对象。|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|类似于 Windows 的类[大小](/windows/desktop/api/windef/ns-windef-tagsize)结构，它实现相对坐标或位置。|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|提供的自动资源清除`GetBuffer`并`ReleaseBuffer`现有调用`CStringT`对象。|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|表示字符串对象的数据。|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|表示`CStringT`对象。|cstringt.h （MFC 取决于） atlstr.h （独立于 MFC）|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|表示一个绝对时间和日期。|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|长时间，在内部存储为中的时间跨度的秒数。|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|表示到接口`CStringT`内存管理器。|atlsimpstr.h|

## <a name="see-also"></a>请参阅

[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
