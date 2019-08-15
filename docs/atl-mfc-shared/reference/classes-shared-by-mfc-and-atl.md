---
title: MFC 和 ATL 共享的类
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491460"
---
# <a name="classes-shared-by-mfc-and-atl"></a>MFC 和 ATL 共享的类

下表列出了 MFC 与 ATL 之间共享的类。

|类|描述|标头文件|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|提供用于管理与文件关联的日期和时间值的方法。|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|提供用于管理与文件关联的相对日期和时间值的方法。|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|表示具有固定字符缓冲区的字符串对象。|cstringt.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|提供增强的位图支持, 包括以 JPEG、GIF、BMP 和可移植网络图形 (PNG) 格式加载和保存图像的功能。|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|封装 OLE 自动化中使用的日期数据类型。|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|表示一个相对时间, 时间跨度。|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|类似于 Windows[点](/windows/win32/api/windef/ns-windef-point)结构的类, 该结构还包含用于操作`CPoint`和`POINT`结构的成员函数。|atltypes.h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|类似于 Windows [RECT](/windows/win32/api/windef/ns-windef-rect)结构的类, 该结构还包含用于操作`CRect`对象和 Windows `RECT`结构的成员函数。|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|表示一个`CSimpleStringT`对象。|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|类似于 Windows [SIZE](/windows/win32/api/windef/ns-windef-size)结构的类, 它实现一个相对坐标或位置。|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|为现有`GetBuffer` `ReleaseBuffer`对象提供和调用的自动资源清理。`CStringT`|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|表示字符串对象的数据。|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|表示一个`CStringT`对象。|cstringt (MFC 依赖) atlstr.h (独立于 MFC)|
|[CTime](../../atl-mfc-shared/reference/ctime-class.md)|表示绝对时间和日期。|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|时间长度, 在内部存储为时间跨度中的秒数。|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|表示`CStringT`内存管理器的接口。|atlsimpstr.h|

## <a name="see-also"></a>请参阅

[ATL/MFC 共享类](../../atl-mfc-shared/atl-mfc-shared-classes.md)
