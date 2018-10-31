---
title: CArchive 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
dev_langs:
- C++
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 88ee9a9e81714064798bbfc652200da9061c6fb0
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059124"
---
# <a name="carchive-class"></a>CArchive 类

可以在这些对象删除后仍然存在以永久二进制形式 （通常为磁盘存储） 中保存的对象的复杂网络。

## <a name="syntax"></a>语法

```
class CArchive
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|创建一个 `CArchive` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CArchive::Abort](#abort)|关闭存档而不引发异常。|
|[CArchive::Close](#close)|刷新写入的数据，并且从断开连接`CFile`。|
|[CArchive::Flush](#flush)|从存档缓冲区刷新写入的数据。|
|[CArchive::GetFile](#getfile)|获取`CFile`对该存档文件的对象指针。|
|[CArchive::GetObjectSchema](#getobjectschema)|从调用`Serialize`函数来确定要反序列化的对象的版本。|
|[CArchive::IsBufferEmpty](#isbufferempty)|确定是否已在 Windows 套接字期间清空缓冲区接收进程。|
|[CArchive::IsLoading](#isloading)|确定是否正在加载存档。|
|[CArchive::IsStoring](#isstoring)|确定是否存储在存档。|
|[CArchive::MapObject](#mapobject)|将对象放在映射的不序列化到文件，但可供引用的子对象。|
|[Carchive:: Read](#read)|读取原始字节。|
|[CArchive::ReadClass](#readclass)|读取使用以前存储的类引用`WriteClass`。|
|[CArchive::ReadObject](#readobject)|调用对象的`Serialize`加载的函数。|
|[CArchive::ReadString](#readstring)|读取单个文本行。|
|[CArchive::SerializeClass](#serializeclass)|读取或写入到的类引用`CArchive`对象，具体取决于的方向`CArchive`。|
|[CArchive::SetLoadParams](#setloadparams)|设置负载数组增长的大小。 加载的任何对象之前或之前必须调用`MapObject`或`ReadObject`调用。|
|[CArchive::SetObjectSchema](#setobjectschema)|设置存档对象中存储的对象架构。|
|[CArchive::SetStoreParams](#setstoreparams)|设置哈希表大小和用于序列化过程中标识唯一对象的映射的块大小。|
|[Carchive:: Write](#write)|写入原始字节。|
|[CArchive::WriteClass](#writeclass)|将引用写入`CRuntimeClass`到`CArchive`。|
|[CArchive::WriteObject](#writeobject)|调用对象的`Serialize`用于存储的函数。|
|[CArchive::WriteString](#writestring)|写入单个文本行。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CArchive::operator &lt;&lt;](#operator_lt_lt)|将对象和基元类型到存档存储。|
|[CArchive::operator &gt;&gt;](#operator_gt_gt)|从存档中加载对象和基元类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CArchive::m_pDocument](#m_pdocument)||

## <a name="remarks"></a>备注

`CArchive` 没有基类。

更高版本，可以从持久性存储区，将其重建在内存中加载对象。 使数据持久的此过程称为"序列化。"

您可以将作为一种二进制流的存档对象。 输入/输出流，如存档与文件相关联，并允许的缓冲的写入和读取到和从存储的数据。 输入/输出流处理的 ASCII 字符序列，但存档处理二进制对象的格式数据的高效、 非冗余。

必须创建[CFile](../../mfc/reference/cfile-class.md)对象，然后您可以创建`CArchive`对象。 此外，必须确保存档文件的加载/存储状态适用于文件的打开模式。 你被限制到每个文件的一个活动存档。

当构造`CArchive`对象，将其附加到类的对象`CFile`（或派生的类），表示打开的文件。 您还指定是否存档将用于加载或存储。 一个`CArchive`基元类型不仅对象的对象可以处理[CObject](../../mfc/reference/cobject-class.md)-派生的类用于序列化。 可序列化的类通常具有`Serialize`成员函数，并且它通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)并[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，如所述类下`CObject`。

重载的提取 ( **>>**) 和插入 ( **<<**) 运算符是方便存档编程接口，它们支持这两种基元类型和`CObject`的派生类。

`CArchive` 此外支持使用 MFC Windows 套接字类编程[CSocket](../../mfc/reference/csocket-class.md)并[CSocketFile](../../mfc/reference/csocketfile-class.md)。 [IsBufferEmpty](#isbufferempty)成员函数支持该使用情况。

有关详细信息`CArchive`，请参阅文章[序列化](../../mfc/serialization-in-mfc.md)并[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CArchive`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="abort"></a>  CArchive::Abort

调用此函数可关闭存档而不引发异常。

```
void Abort ();
```

### <a name="remarks"></a>备注

`CArchive`析构函数通常会调用`Close`，这会将尚未保存任何数据刷新到关联`CFile`对象。 这会导致异常。

时捕获这些异常，它是使用一个好办法`Abort`，以便但`CArchive`对象不会产生其他异常。 在处理异常时,`CArchive::Abort`将不引发异常，故障因为，但不同于[CArchive::Close](#close)，`Abort`忽略故障。

如果您使用了**新**分配`CArchive`对象在堆上，则必须关闭文件后删除它。

### <a name="example"></a>示例

  有关示例，请参阅[CArchive::WriteClass](#writeclass)。

##  <a name="carchive"></a>  CArchive::CArchive

构造`CArchive`对象，并指定是否它将用于加载或存储对象。

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>参数

*pFile*<br/>
一个指向`CFile`的最终源或目标的持久性数据的对象。

*nMode*<br/>
一个标志，指定是否将从加载或存储到存档对象。 *NMode*参数必须具有以下值之一：

- `CArchive::load` 从存档中加载数据。 仅要求`CFile`读取权限。

- `CArchive::store` 将数据保存到存档。 需要`CFile`写入权限。

- `CArchive::bNoFlushOnDelete` 防止自动调用存档`Flush`存档析构函数调用时。 如果设置此标志，您有责任显式调用`Close`析构函数调用之前。 如果不这样做，你的数据将被损坏。

*nBufSize*<br/>
一个整数，以字节为单位指定的内部文件缓冲区的大小。 请注意默认缓冲区大小为 4,096 个字节。 如果你定期存档大型对象，则将提高性能，如果使用较大的缓冲区大小的文件缓冲区大小的倍数。

*lpBuf*<br/>
为用户提供大小的缓冲区的可选指针*nBufSize*。 如果不指定此参数，存档分配从位于本地堆的缓冲区，并将其释放时销毁该对象。 存档不会释放用户提供的缓冲区。

### <a name="remarks"></a>备注

在创建存档后，无法更改此规范。

不能使用`CFile`操作更改文件的状态，直到关闭存档。 此类操作将存档的完整性造成破坏。 你可以在序列化期间随时通过获取从存档文件的文件对象访问的文件指针的位置[GetFile](#getfile)成员函数，然后使用[CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition)函数. 应调用[CArchive::Flush](#flush)之前获取的文件指针的位置。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

##  <a name="close"></a>  CArchive::Close

刷新在缓冲区中剩余的任何数据，关闭存档，并断开与该文件的存档。

```
void Close();
```

### <a name="remarks"></a>备注

允许存档没有进一步的操作。 关闭存档后，可以创建对同一文件的另一个存档，也可以关闭该文件。

成员函数`Close`可确保所有数据都传输从存档到该文件，并使存档不可用。 若要完成从文件传输到存储介质，必须先使用[CFile::Close](../../mfc/reference/cfile-class.md#close)然后销毁`CFile`对象。

### <a name="example"></a>示例

  有关示例，请参阅[CArchive::WriteString](#writestring)。

##  <a name="flush"></a>  CArchive::Flush

强制在要写入到文件的存档缓冲区中剩余的任何数据。

```
void Flush();
```

### <a name="remarks"></a>备注

成员函数`Flush`可确保所有数据从存档都传输到该文件。 必须调用[CFile::Close](../../mfc/reference/cfile-class.md#close)若要完成从文件传输到存储介质。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

##  <a name="getfile"></a>  CArchive::GetFile

获取`CFile`对该存档文件的对象指针。

```
CFile* GetFile() const;
```

### <a name="return-value"></a>返回值

指向常量指针`CFile`中使用的对象。

### <a name="remarks"></a>备注

必须刷新之前使用存档`GetFile`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

##  <a name="getobjectschema"></a>  CArchive::GetObjectSchema

调用此函数从`Serialize`函数来确定当前正在反序列化的对象的版本。

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>返回值

在反序列化，正在读取的对象的版本。

### <a name="remarks"></a>备注

调用此函数时，才有效`CArchive`正在加载对象 ( [CArchive::IsLoading](#isloading)返回非零值)。 它应为中的第一个调用`Serialize`函数并调用仅一次。 返回值为 (UINT)-1 表示未知的版本号。

一个`CObject`的派生的类可能会使用 VERSIONABLE_SCHEMA 结合使用 (使用按位**或者**) 架构版本本身 （采用 IMPLEMENT_SERIAL 宏） 若要创建的"无版本冲突对象，"的对象，即其`Serialize`成员函数可以读取多个版本。 默认框架功能 （不带 VERSIONABLE_SCHEMA) 是版本不匹配时引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

##  <a name="isbufferempty"></a>  CArchive::IsBufferEmpty

调用此成员函数以确定是否存档对象的内部缓冲区为空。

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>返回值

如果存档文件的缓冲区为空，则为非零值否则为 0。

### <a name="remarks"></a>备注

此函数提供以支持使用 MFC Windows 套接字类编程`CSocketFile`。 不需要将其用于与相关联的存档`CFile`对象。

使用的原因`IsBufferEmpty`具有与关联的存档`CSocketFile`对象是存档的缓冲区可能包含多个消息或记录。 收到一条消息后, 应使用`IsBufferEmpty`来控制循环将继续接收数据，直到缓冲区为空。 有关详细信息，请参阅[接收](../../mfc/reference/casyncsocket-class.md#receive)类的成员函数`CAsyncSocket`，其中说明了如何使用`IsBufferEmpty`。

有关详细信息，请参阅[Windows 套接字： 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

##  <a name="isloading"></a>  CArchive::IsLoading

确定存档是否正在加载数据。

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>返回值

如果存档当前正用于加载; 非零值否则为 0。

### <a name="remarks"></a>备注

调用此成员函数`Serialize`存档类的函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

##  <a name="isstoring"></a>  CArchive::IsStoring

确定是否存档将数据存储。

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>返回值

如果存档用于存储; 当前正在使用非零值否则为 0。

### <a name="remarks"></a>备注

调用此成员函数`Serialize`存档类的函数。

如果`IsStoring`存档的状态不为零，则其`IsLoading`状态为 0，反之亦然。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

##  <a name="mapobject"></a>  CArchive::MapObject

调用此成员函数不会真正序列化到文件中，在映射中放置的对象，但可供引用的子对象。

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>参数

*邮政信箱*<br/>
指向要存储的对象的常量指针。

### <a name="remarks"></a>备注

例如，可能会不序列化文档，但将序列化的项的文档的一部分。 通过调用`MapObject`，允许这些项或子对象，若要引用的文档。 此外，可以序列化序列化的子项及其*m_pDocument*后的指针。

您可以调用`MapObject`时将存储到和从加载`CArchive`对象。 `MapObject` 将指定的对象添加到所维护的内部数据结构`CArchive`对象在过程中序列化和反序列化，但与不同[ReadObject](#readobject)并[WriteObject](#writeobject)，不会调用在对象上序列化。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

##  <a name="m_pdocument"></a>  CArchive::m_pDocument

默认情况下，此指针设置为 NULL`CDocument`可设置为任何内容的用户`CArchive`实例想。

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>备注

This 指针的常见用法是传达有关正在序列化的所有对象序列化过程的其他信息。 这通过初始化与该文档的指针来实现 (`CDocument`的派生类) 的正在序列化，如有必要，在文档中的对象可以访问该文档的方式。 也使用此指针`COleClientItem`在序列化过程的对象。

框架集*m_pDocument*向用户发出文件时被序列化文档打开或保存命令。 如果序列化而原因并非文件打开或保存的对象链接与嵌入 (OLE) 容器文档，您必须显式设置*m_pDocument*。 例如，在序列化到剪贴板的容器文档时将执行此操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

##  <a name="operator_lt_lt"></a>  CArchive::operator &lt;&lt;

指示的对象或基元类型到存档存储。

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>返回值

一个`CArchive`引用，以便在单个行上的多个插入运算符。

### <a name="remarks"></a>备注

上面的最后两个版本也是专用于存储 64 位整数。

如果在类实现中，使用 IMPLEMENT_SERIAL 宏，则为重载插入运算符`CObject`调用受保护`WriteObject`。 此函数中，依次调用`Serialize`类的函数。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入运算符 (<<) 支持诊断转储和存储到存档。

### <a name="example"></a>示例

此示例演示如何使用`CArchive`插入运算符 << 与**int**并**长**类型。

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>示例

此示例 2 演示如何使用`CArchive`插入运算符 << 与`CStringT`类型。

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

##  <a name="operator_gt_gt"></a>  CArchive::operator &gt;&gt;

指示的对象或基元类型加载从存档中。

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>返回值

一个`CArchive`引用，以便在单个行上的多个提取运算符。

### <a name="remarks"></a>备注

上面的最后两个版本也是专用于加载 64 位整数。

如果在类实现中，使用 IMPLEMENT_SERIAL 宏，则为提取运算符重载`CObject`调用受保护`ReadObject`（用一个非零值的运行时类的指针） 的函数。 此函数中，依次调用`Serialize`类的函数。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)提取运算符 (>>) 从存档中加载的支持。

### <a name="example"></a>示例

此示例演示如何使用`CArchive`提取运算符 >> 与**int**类型。

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>示例

此示例演示如何使用`CArchive`插入和提取运算符 <\<和 >> 与`CStringT`类型。

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

##  <a name="read"></a>  Carchive:: Read

从存档中读取指定的字节数。

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向将接收从存档中读取的数据的用户提供的缓冲区的指针。

*最*<br/>
无符号的整数，指定的字节数从存档中读取。

### <a name="return-value"></a>返回值

包含实际读取的字节数的无符号的整数。 如果返回值小于请求的数目，已达到文件结尾。 在文件结尾条件不引发任何异常。

### <a name="remarks"></a>备注

存档不解释字节。

可以使用`Read`成员函数中的你`Serialize`用于读取您的对象中包含的普通结构函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

##  <a name="readclass"></a>  CArchive::ReadClass

调用此成员函数以读取对与以前存储的类的引用[WriteClass](#writeclass)。

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>参数

*pClassRefRequested*<br/>
一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对应于请求的类引用的结构。 可以为 NULL。

*pSchema*<br/>
一个指向以前存储的运行时类的架构。

*pObTag*<br/>
对象的唯一标记是指一个数字。 在内部使用的实现[ReadObject](#readobject)。 为高级编程; 仅公开*pObTag*通常应为 NULL。

### <a name="return-value"></a>返回值

一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构。

### <a name="remarks"></a>备注

如果*pClassRefRequested*不为 NULL，`ReadClass`验证是否已存档的类信息是与运行时类兼容。 如果不兼容，`ReadClass`将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

必须使用运行时类[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)并[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); 否则为`ReadClass`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

如果*pSchema*为 NULL，可以通过调用检索的架构的存储类[CArchive::GetObjectSchema](#getobjectschema); 否则为<strong>\*</strong> *pSchema*将包含以前存储的运行时类的架构。

可以使用[SerializeClass](#serializeclass)而不是`ReadClass`，用于处理读取和写入的类引用。

### <a name="example"></a>示例

  有关示例，请参阅[CArchive::WriteClass](#writeclass)。

##  <a name="readobject"></a>  CArchive::ReadObject

从存档读取对象数据，并构造相应类型的对象。

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>参数

*pClass*<br/>
指向常量指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构，它对应于想要读取的对象。

### <a name="return-value"></a>返回值

一个[CObject](../../mfc/reference/cobject-class.md)必须安全地转换为正确的指针使用派生类[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)。

### <a name="remarks"></a>备注

通常情况下调用此函数`CArchive`提取 ( **>>**) 的重载运算符[CObject](../../mfc/reference/cobject-class.md)指针。 `ReadObject`依次调用`Serialize`存档类的函数。

如果您提供了非零*pClass*参数，它通过[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏，则该函数验证是否已存档的对象的运行时类。 假设已在类的实现中使用 IMPLEMENT_SERIAL 宏。

### <a name="example"></a>示例

  有关示例，请参阅[CArchive::WriteObject](#writeobject)。

##  <a name="readstring"></a>  CArchive::ReadString

调用此成员函数以文本数据读入的缓冲区与关联的文件从`CArchive`对象。

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>参数

*rString*<br/>
对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)读取从与 CArchive 对象关联的文件后，将包含生成字符串。

*lpsz*<br/>
指定指向将接收的以 null 结尾的文本字符串的用户提供的缓冲区的指针。

*最*<br/>
指定要读取的字符最大数目。 应为一个小于的大小*lpsz*缓冲区。

### <a name="return-value"></a>返回值

返回布尔值，如果成功，则为 TRUE 的版本中FALSE 否则为。

返回的版本中`LPTSTR`，指向包含的文本数据; 的缓冲区的指针如果已到达文件末尾，则为 NULL。

### <a name="remarks"></a>备注

使用成员函数的版本中*最*参数，缓冲区将保留最多的限制*最*-1 个字符。 读取已停止由回车符和换行符对。 始终删除尾随的换行符字符。 在任一情况下将追加 null 字符 (\0)。

[Carchive:: Read](#read)也是可用的文本模式输入，但它不会终止回车-换行对上。

### <a name="example"></a>示例

  有关示例，请参阅[CArchive::WriteString](#writestring)。

##  <a name="serializeclass"></a>  CArchive::SerializeClass

当你想要存储和加载的基类的版本信息时调用此成员函数。

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>参数

*pClassRef*<br/>
指向基类的运行时类对象的指针。

### <a name="remarks"></a>备注

`SerializeClass` 读取或写入到的类来引用`CArchive`对象，具体取决于的方向`CArchive`。 使用`SerializeClass`来代替[ReadClass](#readclass)并[WriteClass](#writeclass)方便基类对象; 进行序列化`SerializeClass`需要更少的代码和较少的参数。

像`ReadClass`，`SerializeClass`验证是否已存档的类信息是与运行时类兼容。 如果不兼容，`SerializeClass`将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

必须使用运行时类[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)并[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); 否则为`SerializeClass`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏要检索的值*pRuntimeClass*参数。 必须使用的基类[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

##  <a name="setloadparams"></a>  CArchive::SetLoadParams

调用`SetLoadParams`时要读取大量的`CObject`-从存档中派生的对象。

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>参数

*nGrowBy*<br/>
元素槽分配的大小增长是否需要最小数目。

### <a name="remarks"></a>备注

`CArchive` 使用负载数组来解析对存储在存档中的对象的引用。 `SetLoadParams` 可以将负载数组增长的大小设置。

您必须调用`SetLoadParams`加载的任何对象后，或之后[MapObject](#mapobject)或[ReadObject](#readobject)调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="setobjectschema"></a>  CArchive::SetObjectSchema

调用此成员函数可设置为存档对象中存储的对象架构*nSchema*。

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>参数

*nSchema*<br/>
指定对象的架构。

### <a name="remarks"></a>备注

下次调用[GetObjectSchema](#getobjectschema)将返回值存储在*nSchema*。

使用`SetObjectSchema`的高级版本控制功能; 例如，如果你想要强制中读取的特定版本`Serialize`派生类的函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

##  <a name="setstoreparams"></a>  CArchive::SetStoreParams

使用`SetStoreParams`存储大量时`CObject`-派生的对象在存档中。

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>参数

*nHashSize*<br/>
映射的接口指针的哈希表的大小。 应为一个素数。

*nBlockSize*<br/>
指定扩展的参数的内存分配粒度。 应为获得最佳性能的 2 的幂。

### <a name="remarks"></a>备注

`SetStoreParams` 允许您设置的哈希表大小和用于序列化过程中标识唯一对象的映射的块大小。

您必须调用`SetStoreParams`存储的任何对象后，或之后[MapObject](#mapobject)或[WriteObject](#writeobject)调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

##  <a name="write"></a>  Carchive:: Write

将指定的字节数写入到存档。

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向包含要写入到存档的数据的用户提供的缓冲区的指针。

*最*<br/>
一个整数，指定要写入到存档的字节数。

### <a name="remarks"></a>备注

存档不会格式化字节。

可以使用`Write`成员函数中的你`Serialize`函数编写普通结构包含在您的对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

##  <a name="writeclass"></a>  CArchive::WriteClass

使用`WriteClass`存储的版本和类信息的基类在派生类的序列化过程。

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>参数

*pClassRef*<br/>
一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对应于请求的类引用的结构。

### <a name="remarks"></a>备注

`WriteClass` 将引用写入[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)到基类`CArchive`。 使用[CArchive::ReadClass](#readclass)以便检索的引用。

`WriteClass` 验证已存档的类信息是与运行时类兼容。 如果不兼容，`WriteClass`将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

必须使用运行时类[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)并[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); 否则为`WriteClass`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

可以使用[SerializeClass](#serializeclass)而不是`WriteClass`，用于处理读取和写入的类引用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

##  <a name="writeobject"></a>  CArchive::WriteObject

存储指定`CObject`到存档。

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>参数

*邮政信箱*<br/>
指向要存储的对象的常量指针。

### <a name="remarks"></a>备注

通常情况下调用此函数`CArchive`插入 ( **<<**) 的重载运算符`CObject`。 `WriteObject`依次调用`Serialize`存档类的函数。

必须使用 IMPLEMENT_SERIAL 宏来启用存档。 `WriteObject` 将 ASCII 类名写入到存档。 更高版本在加载过程中验证此类名。 特殊的编码方案可防止不必要的类的多个对象的类名重复。 此方案还可以防止冗余存储的目标的多个指针的对象。

确切对象编码 （包括 ASCII 类名称存在） 的方法是实现详细信息，并可以更改在将来版本的库。

> [!NOTE]
>  完成创建、 删除和更新您的所有对象，然后再开始将它们存档。 如果混合使用对象的修改与存档将损坏您的存档。

### <a name="example"></a>示例

有关类的定义`CAge`，有关示例，请参阅[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)。

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

##  <a name="writestring"></a>  CArchive::WriteString

使用此成员函数以将数据从一个缓冲区写入到与关联的文件`CArchive`对象。

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向包含以 null 结尾的文本字符串的缓冲区的指针。

### <a name="remarks"></a>备注

终止 null 字符 (\0) 不会写入该文件;也不新行自动写入。

`WriteString` 到多个条件，包括磁盘已满条件的响应，则会引发异常。

`Write` 也是可用，但而不是终止 null 字符，它将请求的字节数写入到文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 类](../../mfc/reference/csocketfile-class.md)
