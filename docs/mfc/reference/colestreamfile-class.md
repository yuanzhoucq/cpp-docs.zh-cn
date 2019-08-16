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
ms.openlocfilehash: 96e8fee71f02ea750fd8b33f41fd2fd517e9081e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503689"
---
# <a name="colestreamfile-class"></a>COleStreamFile 类

表示作为 OLE 结构化存储一部分的复合文件中的数据流 (`IStream`)。

## <a name="syntax"></a>语法

```
class COleStreamFile : public CFile
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[COleStreamFile:: COleStreamFile](#colestreamfile)|构造 `COleStreamFile` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleStreamFile::Attach](#attach)|将流与对象相关联。|
|[COleStreamFile::CreateMemoryStream](#creatememorystream)|从全局内存创建流并将其与对象关联。|
|[COleStreamFile::CreateStream](#createstream)|创建流并将其与对象关联。|
|[COleStreamFile::Detach](#detach)|解除流与对象的的阻止。|
|[COleStreamFile::GetStream](#getstream)|返回当前流。|
|[COleStreamFile::OpenStream](#openstream)|安全打开流并将其与对象关联。|

## <a name="remarks"></a>备注

`IStorage`对象必须存在, 然后才能打开或创建流, 除非它是内存流。

`COleStreamFile`对象的操作方式与[CFile](../../mfc/reference/cfile-class.md)对象完全相同。

有关操作流和存储的详细信息, 请参阅文章[容器:复合文件](../../mfc/containers-compound-files.md)。

有关详细信息, 请参阅 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream)和[IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>要求

**标头:** afxole

##  <a name="attach"></a>COleStreamFile:: Attach

将提供的 OLE 流与`COleStreamFile`对象相关联。

```
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>参数

*lpStream*<br/>
指向要与对象关联的`IStream`OLE 流 ()。 不能为 NULL。

### <a name="remarks"></a>备注

对象不得与 OLE 流相关联。

有关详细信息, 请参阅 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream) 。

##  <a name="colestreamfile"></a>COleStreamFile:: COleStreamFile

创建一个 `COleStreamFile` 对象。

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>参数

*lpStream*<br/>
指向要与对象关联的 OLE 流的指针。

### <a name="remarks"></a>备注

如果*lpStream*为 NULL, 则对象不与 OLE 流关联, 否则, 对象与提供的 ole 流相关联。

有关详细信息, 请参阅 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream) 。

##  <a name="creatememorystream"></a>COleStreamFile:: CreateMemoryStream

安全地从全局共享内存中创建新流, 其中失败是正常的、预期的情况。

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或指示创建操作的完成状态的 NULL。 如果要监视尝试创建流时生成的可能的异常, 请提供此参数。

### <a name="return-value"></a>返回值

如果成功创建流, 则为非零值;否则为0。

### <a name="remarks"></a>备注

内存由 OLE 子系统分配。

有关详细信息, 请参阅 Windows SDK 中的[CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) 。

##  <a name="createstream"></a>COleStreamFile:: CreateStream

在提供的存储对象中安全地创建一个新流, 其中失败是正常的预期条件。

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lpStorage*<br/>
指向包含要创建的流的 OLE 存储对象。 不能为 NULL。

*lpszStreamName*<br/>
要创建的流的名称。 不能为 NULL。

*nOpenFlags*<br/>
打开流时要使用的访问模式。 默认情况下使用 "独占"、"读/写" 和 "创建" 模式。 有关可用模式的完整列表, 请参阅[CFile:: CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或 NULL。 如果要监视尝试创建流时生成的可能的异常, 请提供此参数。

### <a name="return-value"></a>返回值

如果成功创建流, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果打开失败并且*pError*不为 NULL, 则会引发文件异常。

有关详细信息, 请参阅 Windows SDK 中的[IStorage:: CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) 。

##  <a name="detach"></a>COleStreamFile::D etach

解除流与对象的阻止, 而不关闭流。

```
LPSTREAM Detach();
```

### <a name="return-value"></a>返回值

指向与对象关联的流`IStream`() 的指针。

### <a name="remarks"></a>备注

在程序终止之前, 必须以其他某种方式关闭流。

有关详细信息, 请参阅 Windows SDK 中的[IStream](/windows/win32/api/objidl/nn-objidl-istream) 。

##  <a name="getstream"></a>COleStreamFile:: System.resources.resourcemanager.getstream

调用此函数可返回指向当前流的指针。

```
IStream* GetStream() const;
```

### <a name="return-value"></a>返回值

指向当前流接口的指针 ( [IStream](/windows/win32/api/objidl/nn-objidl-istream))。

##  <a name="openstream"></a>COleStreamFile:: OpenStream

打开现有流。

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>参数

*lpStorage*<br/>
指向包含要打开的流的 OLE 存储对象。 不能为 NULL。

*lpszStreamName*<br/>
要打开的流的名称。 不能为 NULL。

*nOpenFlags*<br/>
打开流时要使用的访问模式。 默认情况下, 使用独占模式和读/写模式。 有关可用模式的完整列表, 请参阅[CFile:: CFile](../../mfc/reference/cfile-class.md#cfile)。

*pError*<br/>
指向[CFileException](../../mfc/reference/cfileexception-class.md)对象或 NULL。 如果要监视尝试打开流时生成的可能异常, 请提供此参数。

### <a name="return-value"></a>返回值

如果成功打开流, 则为非零;否则为0。

### <a name="remarks"></a>备注

如果打开失败并且*pError*不为 NULL, 则会引发文件异常。

有关详细信息, 请参阅 Windows SDK 中的[IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) 。

## <a name="see-also"></a>请参阅

[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
