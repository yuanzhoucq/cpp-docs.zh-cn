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
ms.openlocfilehash: 7fb0ad3eef781be1b5ca358e825c09a88c0109e3
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503828"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 类

表示数据的流 ( [IStream](/windows/desktop/api/objidl/nn-objidl-istream)) 由命名[IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)。

## <a name="syntax"></a>语法

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|构造 `CMonikerFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMonikerFile::Close](#close)|分离和释放流并释放名字对象。|
|[CMonikerFile::Detach](#detach)|分离`IMoniker`从此`CMonikerFile`对象。|
|[CMonikerFile::GetMoniker](#getmoniker)|返回当前名字对象。|
|[CMonikerFile::Open](#open)|打开指定的文件，若要获取的流。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|获取绑定上下文或创建默认初始化绑定上下文。|

## <a name="remarks"></a>备注

一个名字对象包含类似于文件的路径名的信息。 如果您有一个指针指向名字对象的`IMoniker`接口，就可以被标识文件的访问而无需有关文件的实际所在位置的任何其他特定信息。

派生自`COleStreamFile`，`CMonikerFile`采用一个名字对象或可成为名字对象的字符串表示形式，并将绑定到名字对象为其名称的流。 然后，你可以读取和写入该流。 真正目的`CMonikerFile`是能够轻松地访问`IStream`通过名为 s `IMoniker`，以便无需自己，绑定流尚未具有`CFile`到流的功能。

`CMonikerFile` 不能用于绑定到一个流之外的任何内容。 如果你想要将绑定到存储或一个对象，则必须使用`IMoniker`直接接口。

流和名字对象的详细信息，请参阅[COleStreamFile](../../mfc/reference/colestreamfile-class.md)中*MFC 参考*并[IStream](/windows/desktop/api/objidl/nn-objidl-istream)并[IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker)中Windows SDK。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>要求

**标头：** afxole.h

##  <a name="close"></a>  CMonikerFile::Close

调用此函数以分离并释放流并释放名字对象。

```
virtual void Close();
```

### <a name="remarks"></a>备注

可以在未打开或已关闭流上调用。

##  <a name="cmonikerfile"></a>  CMonikerFile::CMonikerFile

构造 `CMonikerFile` 对象。

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>  CMonikerFile::CreateBindContext

调用此函数可创建默认初始化绑定上下文。

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向文件异常的指针。 发生错误，必须先将它设置为原因。

### <a name="return-value"></a>返回值

绑定上下文的指针[IBindCtx](/windows/desktop/api/objidl/nn-objidl-ibindctx)要与绑定，如果成功，否则该值为 NULL。 如果通过打开的实例`IBindHost`接口，从检索的绑定上下文`IBindHost`。 如果没有任何`IBindHost`接口未能返回绑定上下文、 绑定上下文创建。 有关的说明[IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\))接口，请参阅 Windows SDK。

### <a name="remarks"></a>备注

绑定上下文是存储特定的名字对象绑定操作有关的信息的对象。 您可以重写此函数可提供自定义绑定上下文。

##  <a name="detach"></a>  CMonikerFile::Detach

调用此函数可关闭流。

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向文件异常的指针。 发生错误，必须先将它设置为原因。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="getmoniker"></a>  CMonikerFile::GetMoniker

调用此函数可检索对当前名字对象的指针。

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>返回值

指向当前名字对象接口的指针 ( [IMoniker](/windows/desktop/api/objidl/nn-objidl-imoniker))。

### <a name="remarks"></a>备注

由于`CMonikerFile`不是一个接口，返回的指针不会递增引用计数 (通过[AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref))，名字对象被释放时`CMonikerFile`释放对象。 如果你想要保存到名字对象上或自己发布，则必须`AddRef`它。

##  <a name="open"></a>  CMonikerFile::Open

调用此成员函数，以打开文件或名字对象的对象。

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
URL 或要打开的文件的文件名。

*pError*<br/>
指向文件异常的指针。 发生错误，必须先将它设置为原因。

*pMoniker*<br/>
对名字对象接口指针`IMoniker`要用来获取的流。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*LpszURL*无法在 Macintosh 上使用参数。 仅*pMoniker*形式的`Open`可以在 Macintosh 上使用。

可以使用某一 URL 或者文件名*lpszURL*参数。 例如：

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>请参阅

[COleStreamFile 类](../../mfc/reference/colestreamfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)
