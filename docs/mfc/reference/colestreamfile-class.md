---
title: COleStreamFile 类
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: 202f8381361881ce3b8b62f81da5bfb81a1f952d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753754"
---
# <a name="colestreamfile-class"></a>COleStreamFile 类

表示作为 OLE 结构化存储一部分的复合文件中的数据流 (`IStream`)。

## <a name="syntax"></a>语法

```
class COleStreamFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleStream文件：COleStream文件](#colestreamfile)|构造 `COleStreamFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleStream 文件：附加](#attach)|将流与对象关联。|
|[COleStream 文件：创建内存流](#creatememorystream)|从全局内存创建流并将其与对象关联。|
|[COleStream 文件：创建流](#createstream)|创建流并将其与对象关联。|
|[COleStream文件：:D](#detach)|断开流与对象分离。|
|[COleStream 文件：获取流](#getstream)|返回当前流。|
|[COleStream 文件：：打开流](#openstream)|安全地打开流并将其与对象关联。|

## <a name="remarks"></a>备注

必须先`IStorage`存在一个对象，然后才能打开或创建流，除非它是内存流。

`COleStreamFile`对象的操作与[CFile](../../mfc/reference/cfile-class.md)对象完全一样。

有关操作流和存储的详细信息，请参阅文章["容器：复合文件](../../mfc/containers-compound-files.md)"。

有关详细信息，请参阅 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IStorage。](/windows/win32/api/objidl/nn-objidl-istorage)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="colestreamfileattach"></a><a name="attach"></a>COleStream 文件：附加

将提供的 OLE 流与`COleStreamFile`对象关联。

```cpp
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>参数

*lpStream*<br/>
指向要与对象关联的`IStream`OLE 流 （ ）。 不能为 NULL。

### <a name="remarks"></a>备注

对象必须尚未与 OLE 流关联。

有关详细信息，请参阅 Windows SDK 中的[IStream。](/windows/win32/api/objidl/nn-objidl-istream)

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a>COleStream文件：COleStream文件

创建一个 `COleStreamFile` 对象。

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>参数

*lpStream*<br/>
指向要与对象关联的 OLE 流的指针。

### <a name="remarks"></a>备注

如果*lpStream*为 NULL，则该对象不与 OLE 流关联，否则，该对象与提供的 OLE 流相关联。

有关详细信息，请参阅 Windows SDK 中的[IStream。](/windows/win32/api/objidl/nn-objidl-istream)

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a>COleStream 文件：创建内存流

安全地从全局共享内存中创建新流，其中故障是正常的预期条件。

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向指示创建操作的完成状态的[CFileException](../../mfc/reference/cfileexception-class.md)对象或 NULL。 如果要监视尝试创建流生成的可能异常，请提供此参数。

### <a name="return-value"></a>返回值

如果成功创建流，则非零;否则 0。

### <a name="remarks"></a>备注

内存由 OLE 子系统分配。

有关详细信息，请参阅在 Windows SDK 中[创建StreamOnHGlobal。](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal)

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a>COleStream 文件：创建流

在提供的存储对象中安全地创建新流，其中故障是正常的预期条件。

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lp 存储*<br/>
指向包含要创建的流的 OLE 存储对象。 不能为 NULL。

*lpszStream名称*<br/>
要创建的流的名称。 不能为 NULL。

*nOpenFlags*<br/>
打开流时要使用的访问模式。 默认情况下使用独占模式、读/写模式和创建模式。 有关可用模式的完整列表，请参阅[CFile：：CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[文件文件异常](../../mfc/reference/cfileexception-class.md)对象或 NULL。 如果要监视尝试创建流生成的可能异常，请提供此参数。

### <a name="return-value"></a>返回值

如果成功创建流，则非零;否则 0。

### <a name="remarks"></a>备注

如果打开失败，并且*pError*不是 NULL，则将引发文件异常。

有关详细信息，请参阅[IStorage：：](/windows/win32/api/objidl/nf-objidl-istorage-createstream)在 Windows SDK 中创建流。

## <a name="colestreamfiledetach"></a><a name="detach"></a>COleStream文件：:D

在不关闭流的情况下，断开流与对象分离。

```
LPSTREAM Detach();
```

### <a name="return-value"></a>返回值

指向与对象关联的流的指针`IStream`。

### <a name="remarks"></a>备注

在程序终止之前，必须以其他方式关闭流。

有关详细信息，请参阅 Windows SDK 中的[IStream。](/windows/win32/api/objidl/nn-objidl-istream)

## <a name="colestreamfilegetstream"></a><a name="getstream"></a>COleStream 文件：获取流

调用此函数以返回指向当前流的指针。

```
IStream* GetStream() const;
```

### <a name="return-value"></a>返回值

指向当前流接口[（IStream）](/windows/win32/api/objidl/nn-objidl-istream)的指针。

## <a name="colestreamfileopenstream"></a><a name="openstream"></a>COleStream 文件：：打开流

打开现有流。

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lp 存储*<br/>
指向包含要打开的流的 OLE 存储对象。 不能为 NULL。

*lpszStream名称*<br/>
要打开的流的名称。 不能为 NULL。

*nOpenFlags*<br/>
打开流时要使用的访问模式。 默认情况下使用独占和读/写模式。 有关可用模式的完整列表，请参阅[CFile：：CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[文件文件异常](../../mfc/reference/cfileexception-class.md)对象或 NULL。 如果要监视尝试打开流生成的可能异常，则提供此参数。

### <a name="return-value"></a>返回值

如果已成功打开流，则非零;否则 0。

### <a name="remarks"></a>备注

如果打开失败，并且*pError*不是 NULL，则将引发文件异常。

有关详细信息，请参阅[IStorage：：在](/windows/win32/api/objidl/nf-objidl-istorage-openstream)Windows SDK 中打开流。

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
