---
title: CDataPathProperty 类
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 479f5d47d9cff72d36dbd25e434182af1ba01ef4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754653"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 类

实现可异步加载的 OLE 控件属性。

## <a name="syntax"></a>语法

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CDataPath 属性：CDataPath 属性](#cdatapathproperty)|构造 `CDataPathProperty` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDataPath 属性：获取控制](#getcontrol)|检索与`CDataPathProperty`对象关联的异步 OLE 控件。|
|[CDataPath 属性：获取路径](#getpath)|检索属性的路径名称。|
|[CDataPath 属性：：打开](#open)|启动关联 ActiveX （OLE） 控件的异步属性加载。|
|[CDataPath 属性：：重置数据](#resetdata)|调用`CAsyncMonikerFile::OnDataAvailable`以通知容器控件属性已更改。|
|[CDataPath 属性：设置控制](#setcontrol)|设置与属性关联的异步活动X （OLE） 控件。|
|[CDataPath 属性：设置路径](#setpath)|设置属性的路径名称。|

## <a name="remarks"></a>备注

可以在同步启动之后加载异步属性。

类`CDataPathProperty`派生自`CAysncMonikerFile`。 要在 OLE 控件中实现异步属性，请从`CDataPathProperty`派生类并重写[OnData可用](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)。

有关如何在 Internet 应用程序中使用异步名字器和 ActiveX 控件的详细信息，请参阅以下文章：

- [互联网第一步：主动X控制](../../mfc/activex-controls-on-the-internet.md)

- [互联网第一步：异步月友](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream文件](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>要求

**标题：** afxctl.h

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a>CDataPath 属性：CDataPath 属性

构造 `CDataPathProperty` 对象。

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>参数

*pControl*<br/>
指向要与此`CDataPathProperty`对象关联的 OLE 控件对象的指针。

*lpszPath*<br/>
路径可以是绝对的或相对的，用于创建引用属性的实际绝对位置的异步名字对象。 `CDataPathProperty`使用 URL，而不是文件名。 如果需要文件`CDataPathProperty`的对象，则准备`file://`路径。

### <a name="remarks"></a>备注

`COleControl` *pControl*指向的对象由`Open`派生类使用并检索。 如果*pControl*为 NULL，则应`Open`使用`SetControl`设置 与 使用的控件。 如果*lpszPath*为 NULL，则可以在路径中`Open`通过或设置它`SetPath`。

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a>CDataPath 属性：获取控制

调用此成员函数以检索与`COleControl``CDataPathProperty`对象关联的对象。

```
COleControl* GetControl();
```

### <a name="return-value"></a>返回值

返回指向与对象关联的 OLE 控件的`CDataPathProperty`指针。 NULL（如果不是控件）是关联的。

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a>CDataPath 属性：获取路径

调用此成员函数以检索路径、在构造`CDataPathProperty`对象时设置或在 中`Open`指定，或在 上一次对`SetPath`成员函数的调用中指定。

```
CString GetPath() const;
```

### <a name="return-value"></a>返回值

将路径名称返回到属性本身。 如果未指定路径，则可以为空。

## <a name="cdatapathpropertyopen"></a><a name="open"></a>CDataPath 属性：：打开

调用此成员函数以启动关联控件的异步属性加载。

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*pControl*<br/>
指向要与此`CDataPathProperty`对象关联的 OLE 控件对象的指针。

*pError*<br/>
指向文件异常的指针。 如果出现错误，将设置为原因。

*lpszPath*<br/>
路径可以是绝对的或相对的，用于创建引用属性的实际绝对位置的异步名字对象。 `CDataPathProperty`使用 URL，而不是文件名。 如果需要文件`CDataPathProperty`的对象，则准备`file://`路径。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

函数尝试从控件获取`IBindHost`接口。

在调用`Open`没有路径之前，必须设置属性路径的值。 这在构造对象时或调用`SetPath`成员函数可以完成。

在没有控件`Open`的情况下调用之前，可以与对象关联 ActiveX 控件（以前称为 OLE 控件）。 这可以在构造对象时完成，也可以调用`SetControl`。

[CAsyncMonikerFile 的所有过载功能：：打开](../../mfc/reference/casyncmonikerfile-class.md#open)也可从`CDataPathProperty`获得。

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a>CDataPath 属性：：重置数据

调用此函数以通知`CAsyncMonikerFile::OnDataAvailable`容器控件属性已更改，并且以异步方式加载的所有信息不再有用。

```
virtual void ResetData();
```

### <a name="remarks"></a>备注

应重新启动打开。 派生类可以针对不同的默认值重写此函数。

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a>CDataPath 属性：设置控制

调用此成员函数将异步 OLE 控件与`CDataPathProperty`对象关联。

```cpp
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>参数

*pControl*<br/>
指向要与属性关联的异步 OLE 控件的指针。

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a>CDataPath 属性：设置路径

调用此成员函数以设置属性的路径名称。

```cpp
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
路径（可以是绝对的或相对的）与异步加载的属性。 `CDataPathProperty`使用 URL，而不是文件名。 如果需要文件`CDataPathProperty`的对象，则准备`file://`路径。

## <a name="see-also"></a>请参阅

[MFC 样本图像](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)
