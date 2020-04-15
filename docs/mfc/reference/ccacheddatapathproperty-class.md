---
title: CCachedDataPathProperty 类
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352369"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty 类

实现异步传输并在内存文件中缓冲的 OLE 控件属性。

## <a name="syntax"></a>语法

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CCached数据路径属性：CCachedDataPath属性](#ccacheddatapathproperty)|构造 `CCachedDataPathProperty` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CCachedDataPath 属性：：m_Cache](#m_cache)|`CMemFile`要在其中缓存数据的对象。|

## <a name="remarks"></a>备注

内存文件存储在 RAM 中而不是磁盘上，可用于快速临时传输。

与`CAysncMonikerFile`和`CDataPathProperty``CCachedDataPathProperty`一起提供了在 OLE 控件中使用异步名字器的功能。 对于`CCachedDataPathProperty`对象，您可以从 URL 或文件源异步传输数据，并通过`m_Cache`公共变量将其存储在内存文件中。 所有数据都存储在内存文件中，除非您想要监视通知并响应，否则无需覆盖[OnDataFor。](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) 例如，如果要传输较大的 。GIF 文件，并希望通知您的控件，更多的数据已经到来，它应该重新绘制本身，重写`OnDataAvailable`以发出通知。

类`CCachedDataPathProperty`派生自`CDataPathProperty`。

有关如何在 Internet 应用程序中使用异步名字器和 ActiveX 控件的详细信息，请参阅以下主题：

- [互联网第一步：主动X控制](../../mfc/activex-controls-on-the-internet.md)

- [互联网第一步：异步月友](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream文件](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCached数据路径属性：CCachedDataPath属性

构造 `CCachedDataPathProperty` 对象。

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>参数

*pControl*<br/>
指向要与此`CCachedDataPathProperty`对象关联的 ActiveX 控件对象的指针。

*lpszPath*<br/>
路径可以是绝对的或相对的，用于创建引用属性的实际绝对位置的异步名字对象。 `CCachedDataPathProperty`使用 URL，而不是文件名。 如果需要文件`CCachedDataPathProperty`的对象，则file://路径进行预准备。

### <a name="remarks"></a>备注

`COleControl` *pControl*指向的对象由[Open](../../mfc/reference/cdatapathproperty-class.md#open)使用，并由派生类检索。 如果*pControl*为 NULL，则应`Open`使用[SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)设置 与 中使用的控件。 如果*lpszPath*为 NULL，则可以在路径中`Open`通过路径或使用[SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)设置它。

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPath 属性：：m_Cache

包含缓存数据的内存文件的类名。

```
CMemFile m_Cache;
```

### <a name="remarks"></a>备注

内存文件存储在 RAM 中，而不是存储在磁盘上。

## <a name="see-also"></a>另请参阅

[CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty 类](../../mfc/reference/cdatapathproperty-class.md)
