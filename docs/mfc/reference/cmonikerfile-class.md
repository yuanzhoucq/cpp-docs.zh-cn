---
title: CMonikerFile 类
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319775"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 类

表示由[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)命名的数据流 （ [IStream](/windows/win32/api/objidl/nn-objidl-istream)）。

## <a name="syntax"></a>语法

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMoniker文件：CMoniker文件](#cmonikerfile)|构造 `CMonikerFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMoniker 文件：关闭](#close)|分离并释放流并释放名字对象。|
|[CMoniker文件：:D](#detach)|从此`CMonikerFile`对象`IMoniker`分离 。|
|[CMoniker文件：获取莫尼克尔](#getmoniker)|返回当前名字对象。|
|[CMoniker文件：：打开](#open)|打开指定的文件以获取流。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CMoniker 文件：：创建绑定上下文](#createbindcontext)|获取绑定上下文或创建默认初始化绑定上下文。|

## <a name="remarks"></a>备注

名字对象包含的信息与文件的路径名称非常类似。 如果具有指向名字对象接口的`IMoniker`指针，则可以访问已标识的文件，而无需提供有关文件实际位置的任何其他特定信息。

派生自`COleStreamFile` `CMonikerFile` ，获取可以将其转换为名字对象并绑定到名字对象为名称的流的字符串表示形式。 然后，您可以读取和写入该流。 的真正目的是`CMonikerFile`提供对 s`IStream``IMoniker`命名的 s 的简单访问，这样您不必自己绑定到流，而又对流具有`CFile`功能。

`CMonikerFile`不能用于绑定到流以外的任何内容。 如果要绑定到存储或对象，必须直接使用接口`IMoniker`。

有关流和名字的详细信息，请参阅*MFC 参考*中的[COleStreamFile](../../mfc/reference/colestreamfile-class.md)以及 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IMoniker。](/windows/win32/api/objidl/nn-objidl-imoniker)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStream文件](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMoniker 文件：关闭

调用此函数以分离和释放流并释放名字对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

可以在未打开或已关闭的流上调用。

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMoniker文件：CMoniker文件

构造 `CMonikerFile` 对象。

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>CMoniker 文件：：创建绑定上下文

调用此函数以创建默认初始化绑定上下文。

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向文件异常的指针。 如果出现错误，它将设置为原因。

### <a name="return-value"></a>返回值

指向绑定上下文 IBindCtx 的指针，如果成功，则与绑定上下文[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)绑定;否则 NULL。 如果实例是使用接口打开的`IBindHost`，则从 中检索绑定上下文`IBindHost`。 如果没有`IBindHost`接口或接口无法返回绑定上下文，则创建绑定上下文。 有关[IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\))接口的说明，请参阅 Windows SDK。

### <a name="remarks"></a>备注

绑定上下文是存储有关特定名字绑定操作的信息的对象。 您可以重写此函数以提供自定义绑定上下文。

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMoniker文件：:D

调用此函数以关闭流。

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向文件异常的指针。 如果出现错误，它将设置为原因。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMoniker文件：获取莫尼克尔

调用此函数以检索指向当前名字对象的指针。

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>返回值

指向当前名字接口[（IMoniker） 的](/windows/win32/api/objidl/nn-objidl-imoniker)指针。

### <a name="remarks"></a>备注

由于`CMonikerFile`不是接口，返回的指针不会增加引用计数（通过[AddRef），](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)并且在释放`CMonikerFile`对象时释放名字对象。 如果你想抓住名字或释放它自己，你必须`AddRef`它。

## <a name="cmonikerfileopen"></a><a name="open"></a>CMoniker文件：：打开

调用此成员函数以打开文件或名字对象。

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lpszURL*<br/>
要打开的文件的 URL 或文件名。

*pError*<br/>
指向文件异常的指针。 如果出现错误，它将设置为原因。

*普莫尼克尔*<br/>
指向用于获取流的名字接口`IMoniker`的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*lpszURL*参数不能在 Macintosh 上使用。 只有*pMoniker*的`Open`格式可以在 Macintosh 上使用。

可以使用 URL 或文件名进行*lpszURL*参数。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>另请参阅

[COleStreamFile 类](../../mfc/reference/colestreamfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)
