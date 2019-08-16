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
ms.openlocfilehash: 56283b56a1c0832d34ce23c7db47c47d9480aec8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504570"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 类

表示由[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)命名的数据流 ( [IStream](/windows/win32/api/objidl/nn-objidl-istream))。

## <a name="syntax"></a>语法

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMonikerFile:: CMonikerFile](#cmonikerfile)|构造 `CMonikerFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMonikerFile::Close](#close)|分离并释放流并释放标记。|
|[CMonikerFile::Detach](#detach)|`IMoniker` 从此`CMonikerFile`对象分离。|
|[CMonikerFile::GetMoniker](#getmoniker)|返回当前的名字对象。|
|[CMonikerFile::Open](#open)|打开指定的文件以获取流。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|获取绑定上下文或创建默认的已初始化绑定上下文。|

## <a name="remarks"></a>备注

名字对象包含的信息与文件的路径名非常类似。 如果有指向名字对象`IMoniker`接口的指针, 则可以获取对已标识文件的访问权限, 而无需使用有关文件实际位置的任何其他特定信息。

从`COleStreamFile`派生, `CMonikerFile`获取一个名字对象或字符串表示形式, 它可以将其转换为名字对象, 并绑定到该名字对象为其名称的流。 然后, 你可以读取和写入该流。 的真正用途`CMonikerFile`是提供对的对`IStream`的`IMoniker`简单访问, 以便你无需自行绑定到流, 而是具有`CFile`流功能。

`CMonikerFile`不能用于绑定到流之外的任何内容。 如果要绑定到存储或对象, 则必须直接使用`IMoniker`接口。

有关流和名字对象的详细信息, 请参阅*MFC 参考*中的[COleStreamFile](../../mfc/reference/colestreamfile-class.md)和 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>要求

**标头:** afxole

##  <a name="close"></a>CMonikerFile:: Close

调用此函数可分离并释放流并释放标记。

```
virtual void Close();
```

### <a name="remarks"></a>备注

可对未打开或已关闭的流调用。

##  <a name="cmonikerfile"></a>CMonikerFile:: CMonikerFile

构造 `CMonikerFile` 对象。

```
CMonikerFile();
```

##  <a name="createbindcontext"></a>CMonikerFile:: CreateBindContext

调用此函数可创建默认的已初始化绑定上下文。

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向文件异常的指针。 如果发生错误, 则会将其设置为原因。

### <a name="return-value"></a>返回值

一个指针, 指向要绑定的绑定上下文[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) , 如果成功, 则为; 否则为。否则为 NULL。 如果使用`IBindHost`接口打开实例, 将`IBindHost`从中检索绑定上下文。 如果没有`IBindHost`接口或接口未能返回绑定上下文, 则将创建一个绑定上下文。 有关[IBindHost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\))接口的说明, 请参阅 Windows SDK。

### <a name="remarks"></a>备注

绑定上下文是一个对象, 该对象存储有关特定名字对象绑定操作的信息。 可以重写此函数以提供自定义绑定上下文。

##  <a name="detach"></a>CMonikerFile::D etach

调用此函数可关闭流。

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向文件异常的指针。 如果发生错误, 则会将其设置为原因。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

##  <a name="getmoniker"></a>CMonikerFile:: GetMoniker

调用此函数可检索指向当前名字对象的指针。

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>返回值

指向当前名字对象接口 ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)) 的指针。

### <a name="remarks"></a>备注

由于`CMonikerFile`不是接口, 因此返回的指针不会递增引用计数 (通过[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)), 并且在释放`CMonikerFile`对象时将释放标记。 如果要保存到名字对象或自行发布, 则必须`AddRef`这样做。

##  <a name="open"></a>CMonikerFile:: Open

调用此成员函数以打开文件或名字对象对象。

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
指向文件异常的指针。 如果发生错误, 则会将其设置为原因。

*pMoniker*<br/>
指向用于获取流的名字`IMoniker`对象接口的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*LpszURL*参数不能在 Macintosh 上使用。 只能在 Macintosh 上使用`Open`的 pMoniker 形式。

可以对*lpszURL*参数使用 URL 或文件名。 例如:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- 或 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>请参阅

[COleStreamFile 类](../../mfc/reference/colestreamfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 类](../../mfc/reference/casyncmonikerfile-class.md)
