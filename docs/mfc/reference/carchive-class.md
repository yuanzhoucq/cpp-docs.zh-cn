---
title: CArchive 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 46d30e38674d10aecdfdbf7be91c48063ba9f493
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377068"
---
# <a name="carchive-class"></a>CArchive 类

允许您以永久二进制形式（通常是磁盘存储）保存复杂的对象网络，这些二进制形式在删除这些对象后仍然存在。

## <a name="syntax"></a>语法

```
class CArchive
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C存档：C存档](#carchive)|创建一个 `CArchive` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C存档：：中止](#abort)|关闭存档而不引发异常。|
|[C存档：关闭](#close)|刷新不写入的数据并从 断开连接`CFile`。|
|[C存档：冲洗](#flush)|从存档缓冲区刷新不写入的数据。|
|[C存档：获取文件](#getfile)|获取`CFile`此存档的对象指针。|
|[C存档：获取对象架构](#getobjectschema)|从`Serialize`函数调用以确定正在反序列化的对象的版本。|
|[C存档：：是缓冲区空](#isbufferempty)|确定缓冲区在 Windows 套接字接收过程中是否已清空。|
|[C存档：正在加载](#isloading)|确定存档是否正在加载。|
|[C存档：正在存储](#isstoring)|确定存档是否正在存储。|
|[C 存档：mapObject](#mapobject)|在地图中放置未序列化到文件但可用于子对象引用的对象。|
|[C存档：阅读](#read)|读取原始字节。|
|[C存档：阅读类](#readclass)|读取以前与 一起`WriteClass`存储的类引用。|
|[C存档：读取对象](#readobject)|调用对象的`Serialize`函数以进行加载。|
|[C存档：：阅读字符串](#readstring)|读取一行文本。|
|[C存档：序列化类](#serializeclass)|根据 的方向读取或写入对`CArchive`对象的类引用。 `CArchive`|
|[C存档：：设置加载参数](#setloadparams)|设置负载阵列增长的大小。 必须在加载任何对象之前、加载或之前`MapObject`调用。 `ReadObject`|
|[C存档：设置对象架构](#setobjectschema)|设置存储在存档对象中的对象架构。|
|[C存档：：设置存储参数](#setstoreparams)|设置哈希表大小和映射的块大小，用于在序列化过程中标识唯一对象。|
|[C存档：写入](#write)|写入原始字节。|
|[C存档：写入类](#writeclass)|写入 对 的`CRuntimeClass``CArchive`引用。|
|[C存档：写入对象](#writeobject)|调用对象的`Serialize`函数进行存储。|
|[C存档：：写入字符串](#writestring)|写入一行文本。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[C存档：：运算符&lt;&lt;](#operator_lt_lt)|将对象和基元类型存储到存档中。|
|[C存档：：运算符&gt;&gt;](#operator_gt_gt)|从存档加载对象和基元类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C 存档：m_pDocument](#m_pdocument)||

## <a name="remarks"></a>备注

`CArchive`没有基类。

稍后，可以从持久存储加载对象，在内存中重新构建它们。 使数据持久化的过程称为"序列化"。

您可以将存档对象视为一种二进制流。 与输入/输出流一样，存档与文件相关联，并允许缓冲写入和读取数据，并从存储中读取数据。 输入/输出流处理 ASCII 字符序列，但存档以有效的非冗余格式处理二进制对象数据。

必须先创建[CFile](../../mfc/reference/cfile-class.md)对象，然后才能创建`CArchive`对象。 此外，必须确保存档的加载/存储状态与文件的打开模式兼容。 每个文件只能使用一个活动存档。

构造`CArchive`对象时，将其附加到表示打开文件的类`CFile`（或派生类）的对象。 您还可以指定存档是否将用于加载或存储。 对象`CArchive`不仅可以处理基元类型，还可以处理用于序列化的[CObject](../../mfc/reference/cobject-class.md)派生类的对象。 可序列化类通常`Serialize`具有成员函数，它通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，如类`CObject`下所述。

重载提取 （ **>>**） 和**<<** 插入 （ ） 运算符是支持基元类型和`CObject`派生类的方便的存档编程接口。

`CArchive`还支持使用 MFC Windows 套接字类 CSocket 和[CSocketFile](../../mfc/reference/csocket-class.md)进行编程。 [CSocketFile](../../mfc/reference/csocketfile-class.md) [IsBufferEmpty](#isbufferempty)成员函数支持该用法。

有关 的详细信息`CArchive`，请参阅文章[序列化和](../../mfc/serialization-in-mfc.md)Windows[套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CArchive`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="carchiveabort"></a><a name="abort"></a>C存档：：中止

调用此函数以关闭存档，而不会引发异常。

```
void Abort ();
```

### <a name="remarks"></a>备注

析`CArchive`构函数通常会调用`Close`，这将刷新尚未保存到关联`CFile`对象的任何数据。 这可能会导致异常。

捕获这些异常时，最好使用`Abort`，以便销毁`CArchive`对象不会导致进一步的异常。 处理异常时，`CArchive::Abort`不会引发故障异常，因为与[CArchive：：Close](#close)不同，`Abort`忽略失败。

如果使用**new**在堆上`CArchive`分配对象，则必须在关闭文件后将其删除。

### <a name="example"></a>示例

  请参阅[CArchive：：WriteClass](#writeclass)的示例。

## <a name="carchivecarchive"></a><a name="carchive"></a>C存档：C存档

构造`CArchive`对象并指定该对象是否用于加载或存储对象。

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>参数

*pFile*<br/>
指向对象作为`CFile`持久数据的最终源或目标的指针。

*nMode*<br/>
指定对象是从存档加载还是存储到存档的标志。 *nMode*参数必须具有以下值之一：

- `CArchive::load`从存档加载数据。 只需要`CFile`读取权限。

- `CArchive::store`将数据保存到存档中。 需要`CFile`写入权限。

- `CArchive::bNoFlushOnDelete`防止在调用存档析构`Flush`函数时自动调用存档。 如果设置此标志，则负责在调用析构函数之前`Close`显式调用。 如果没有，您的数据将损坏。

*nBufSize*<br/>
指定内部文件缓冲区大小的整数（以字节为单位）。 请注意，默认缓冲区大小为 4，096 字节。 如果例行存档大型对象，则如果使用较大的缓冲区大小（是文件缓冲区大小的倍数）来提高性能。

*lpBuf*<br/>
指向用户提供的大小*nBufSize*缓冲区的可选指针。 如果不指定此参数，存档将从本地堆分配缓冲区，并在对象销毁时释放它。 存档不会释放用户提供的缓冲区。

### <a name="remarks"></a>备注

创建存档后，无法更改此规范。

在关闭存档之前`CFile`，不得使用操作来更改文件的状态。 任何此类操作都将损坏存档的完整性。 在序列化期间，您可以随时从[GetFile](#getfile)成员函数获取存档的文件对象，然后使用[CFile：get定位](../../mfc/reference/cfile-class.md#getposition)函数来访问文件指针的位置。 在获取文件指针的位置之前，应调用[CArchive：：Flush。](#flush)

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>C存档：关闭

刷新缓冲区中剩余的所有数据，关闭存档，并将存档与文件断开连接。

```
void Close();
```

### <a name="remarks"></a>备注

不允许对存档执行进一步操作。 关闭存档后，可以为同一文件创建另一个存档，也可以关闭该文件。

成员函数`Close`可确保所有数据从存档传输到文件，并使存档不可用。 要完成从文件传输到存储介质，必须首先使用[CFile：：关闭](../../mfc/reference/cfile-class.md#close)，然后销毁`CFile`对象。

### <a name="example"></a>示例

  请参阅[CArchive：：写入字符串](#writestring)的示例。

## <a name="carchiveflush"></a><a name="flush"></a>C存档：冲洗

强制将存档缓冲区中剩余的任何数据写入文件。

```
void Flush();
```

### <a name="remarks"></a>备注

成员函数`Flush`可确保所有数据从存档传输到文件。 您必须调用[CFile：：关闭](../../mfc/reference/cfile-class.md#close)才能完成从文件传输到存储介质。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>C存档：获取文件

获取`CFile`此存档的对象指针。

```
CFile* GetFile() const;
```

### <a name="return-value"></a>返回值

指向正在使用的对象的`CFile`常量指针。

### <a name="remarks"></a>备注

在使用`GetFile`之前，必须刷新存档。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>C存档：获取对象架构

从`Serialize`函数调用此函数以确定当前正在反序列化的对象的版本。

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>返回值

在反序列化期间，正在读取的对象的版本。

### <a name="remarks"></a>备注

仅当加载对象时，`CArchive`调用此函数才有效[（CArchive：：IsLoaded](#isloading)返回非零）。 它应该是函数中的第一个调用`Serialize`，并且只调用一次。 （UINT）-1 的返回值表示版本号未知。

派生类可以使用VERSIONABLE_SCHEMA与架构版本本身（在IMPLEMENT_SERIAL宏中）组合（使用位**或**）来创建一个"可版本对象"，即其成员`Serialize`函数可以读取多个版本的对象。 `CObject` 默认框架功能（无VERSIONABLE_SCHEMA）是在版本不匹配时引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>C存档：：是缓冲区空

调用此成员函数以确定存档对象的内部缓冲区是否为空。

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>返回值

如果存档的缓冲区为空，则非零;否则 0。

### <a name="remarks"></a>备注

此功能用于支持 MFC Windows 套接字类`CSocketFile`的编程。 不需要将其用于与`CFile`对象关联的存档。

与与`CSocketFile`对象关联的`IsBufferEmpty`存档一起使用的原因是存档的缓冲区可能包含多条消息或记录。 收到一条消息后，应使用`IsBufferEmpty`来控制继续接收数据的循环，直到缓冲区为空。 有关详细信息，请参阅 类`CAsyncSocket`的`IsBufferEmpty`[接收](../../mfc/reference/casyncsocket-class.md#receive)成员函数，其中演示如何使用 。

有关详细信息，请参阅[Windows 套接字：使用带存档的套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="carchiveisloading"></a><a name="isloading"></a>C存档：正在加载

确定存档是否正在加载数据。

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>返回值

如果存档当前用于加载，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数由存档的类`Serialize`的函数调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>C存档：正在存储

确定存档是否存储数据。

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>返回值

如果存档当前用于存储，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数由存档的类`Serialize`的函数调用。

如果存档`IsStoring`的状态为非零，则其`IsLoading`状态为 0，反之亦然。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>C 存档：mapObject

调用此成员函数，将未真正序列化到文件的地图中的对象放置，但可用于子对象引用的对象。

```
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>参数

*Pob*<br/>
指向要存储的对象的常量指针。

### <a name="remarks"></a>备注

例如，您可能不会序列化文档，但可以序列化作为文档一部分的项。 通过调用`MapObject`，允许这些项目或子对象引用文档。 此外，序列化子项可以序列化其*m_pDocument*回指针。

您可以在存储对象`MapObject`时调用`CArchive`对象并从对象加载。 `MapObject`将指定对象添加到`CArchive`对象在序列化和反序列化期间维护的内部数据结构中，但与[ReadObject](#readobject)和[WriteObject](#writeobject)不同，它不调用对象上的序列化。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>C 存档：m_pDocument

默认情况下，此指针可以`CDocument`设置为`CArchive`实例用户想要的任何指针。

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>备注

此指针的常见用法是向所有要序列化的对象传达有关序列化过程的其他信息。 这是通过使用正在序列化的文档（`CDocument`派生类）初始化指针来实现的，这样文档中的对象可以在必要时访问文档。 此指针在序列化期间`COleClientItem`也由对象使用。

当用户发出文件打开或保存命令时，框架将*m_pDocument*文档序列化。 如果出于文件打开或保存等原因序列化对象链接和嵌入 （OLE） 容器文档，则必须显式设置*m_pDocument*。 例如，在将容器文档序列化到剪贴板时，可以执行此操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>C存档：：运算符&lt;&lt;

将指示的对象或基元类型存储到存档中。

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

在`CArchive`一行上启用多个插入运算符的引用。

### <a name="remarks"></a>备注

上面的最后两个版本专门用于存储 64 位整数。

如果在类实现中使用IMPLEMENT_SERIAL宏，则插入运算符重载以`CObject`调用受保护的`WriteObject`。 此函数反过来调用类`Serialize`的函数。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入运算符 （<<） 支持诊断转储并存储到存档。

### <a name="example"></a>示例

此示例演示了插入运算符 << `CArchive` **int**和**长**类型。

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>示例

此示例 2 演示了使用`CArchive`插入运算符 << `CStringT`的类型。

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>C存档：：运算符&gt;&gt;

从存档加载指示的对象或基元类型。

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

在`CArchive`一行上启用多个提取运算符的引用。

### <a name="remarks"></a>备注

上面的最后两个版本专门用于加载 64 位整数。

如果在类实现中使用IMPLEMENT_SERIAL宏，则提取运算符将重载以`CObject`调用受保护的`ReadObject`函数（使用非零运行时类指针）。 此函数反过来调用类`Serialize`的函数。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)提取运算符 （>>） 支持从存档加载。

### <a name="example"></a>示例

此示例演示了提取运算符 >> `CArchive` **int**类型的使用。

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>示例

此示例演示了插入和提取运算符`CArchive`的使用，<，\<并且 >> 与类型。 `CStringT`

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>C存档：阅读

从存档中读取指定数量的字节。

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向用户提供的缓冲区的指针，用于接收从存档读取的数据。

*nMax*<br/>
一个未签名的整数，用于指定要从存档中读取的字节数。

### <a name="return-value"></a>返回值

包含实际读取字节数的无符号整数。 如果返回值小于请求的数量，则已达到文件结尾。 文件结尾条件上不引发异常。

### <a name="remarks"></a>备注

存档不解释字节。

可以使用`Read``Serialize`函数中的成员函数读取对象中包含的普通结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>C存档：阅读类

调用此成员函数以读取对以前使用[WriteClass](#writeclass)存储的类的引用。

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>参数

*pClassRef 请求*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针，对应于请求的类引用。 可以为 NULL。

*pSchema*<br/>
指向以前存储的运行时类的架构的指针。

*pObTag*<br/>
引用对象的唯一标记的数字。 内部使用[ReadObject](#readobject)的实现。 仅用于高级编程;*pObTag*通常应为 NULL。

### <a name="return-value"></a>返回值

指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针。

### <a name="remarks"></a>备注

如果*pClassRef 请求*不是`ReadClass`NULL，请验证存档的类信息是否与运行时类兼容。 如果它不兼容，`ReadClass`将抛出一个[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的运行时类必须使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否则，`ReadClass`将抛出[一个CNot被支持例外](../../mfc/reference/cnotsupportedexception-class.md)。

如果*pSchema*为 NULL，则可以通过调用[CArchive：：getObjectSchema](#getobjectschema)来检索存储类的架构。否则<strong>\*</strong>*，pSchema*将包含以前存储的运行时类的架构。

可以使用[序列化类](#serializeclass)而不是`ReadClass`，来处理类引用的读取和写入。

### <a name="example"></a>示例

  请参阅[CArchive：：WriteClass](#writeclass)的示例。

## <a name="carchivereadobject"></a><a name="readobject"></a>C存档：读取对象

从存档中读取对象数据并构造相应类型的对象。

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>参数

*pClass*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的常量指针，对应于您预期读取的对象。

### <a name="return-value"></a>返回值

必须使用[CObject：：IsKinds](../../mfc/reference/cobject-class.md#iskindof)安全地强制转换为正确的派生类的[CObject](../../mfc/reference/cobject-class.md)指针。

### <a name="remarks"></a>备注

此函数通常由`CArchive`[CObject](../../mfc/reference/cobject-class.md)指针**>>** 的提取 （ ） 运算符重载调用。 `ReadObject`，反过来，`Serialize`调用存档的类的功能。

如果提供非零*pClass*参数（由[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏获取，则该函数将验证存档对象的运行时类。 这假定您在类的实现中使用了IMPLEMENT_SERIAL宏。

### <a name="example"></a>示例

  请参阅[CArchive：：WriteObject](#writeobject)的示例。

## <a name="carchivereadstring"></a><a name="readstring"></a>C存档：：阅读字符串

调用此成员函数从与对象关联的文件中将文本数据读取到缓冲区中`CArchive`。

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>参数

*rString*<br/>
对[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用，该字符串将在从与 CArchive 对象关联的文件中读取后包含该字符串。

*lpsz*<br/>
指定指向用户提供的缓冲区的指针，该缓冲区将接收 null 终止的文本字符串。

*nMax*<br/>
指定要读取的最大字符数。 应小于*lpsz*缓冲区的大小。

### <a name="return-value"></a>返回值

在返回 BOOL 的版本中，如果成功，为 TRUE;否则。

在返回`LPTSTR`的版本中，将指向包含文本数据的缓冲区的指针;如果达到文件结尾，则为 NULL。

### <a name="remarks"></a>备注

在具有*nMax*参数的成员函数版本中，缓冲区将最多保留*nMax* - 1 个字符的限制。 读取由滑车返回线进给对停止。 尾随换行符始终被删除。 在这两种情况下都附加了空字符 （"\0"）。

[CArchive：：读取](#read)也可用于文本模式输入，但它不会在回车返回行馈送对上终止。

### <a name="example"></a>示例

  请参阅[CArchive：：写入字符串](#writestring)的示例。

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>C存档：序列化类

如果要存储和加载基类的版本信息，请调用此成员函数。

```
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>参数

*pClassRef*<br/>
指向基类的运行时类对象的指针。

### <a name="remarks"></a>备注

`SerializeClass`根据`CArchive``CArchive`的方向读取或写入对对象的类的引用。 使用`SerializeClass` [ReadClass](#readclass)和[WriteClass](#writeclass)作为序列化基类对象的便捷方法;`SerializeClass`需要更少的代码和更少的参数。

与`ReadClass``SerializeClass`样，验证存档的类信息是否与运行时类兼容。 如果它不兼容，`SerializeClass`将抛出一个[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的运行时类必须使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否则，`SerializeClass`将抛出[一个CNot被支持例外](../../mfc/reference/cnotsupportedexception-class.md)。

使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏检索*pRuntimeClass 参数*的值。 基类必须使用了[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>C存档：：设置加载参数

当您`SetLoadParams`要从存档中读取大量`CObject`派生对象时调用。

```
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>参数

*nGrowBy*<br/>
如果需要增加大小，要分配的最小元素槽数。

### <a name="remarks"></a>备注

`CArchive`使用负载数组解析对存档中存储对象的引用。 `SetLoadParams`允许您设置负载数组增长的大小。

在加载任何对象`SetLoadParams`或调用 MapObject 或[ReadObject](#mapobject) [ReadObject](#readobject)之后，不得调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>C存档：设置对象架构

调用此成员函数将存储在存档对象中的对象架构设置为*nSchema*。

```
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>参数

*nSchema*<br/>
指定对象的架构。

### <a name="remarks"></a>备注

下一次调用[GetObjectSchema](#getobjectschema)将返回存储在*nSchema*中的值。

用于`SetObjectSchema`高级版本控制;例如，当您要强制在派生类的`Serialize`函数中读取特定版本时。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>C存档：：设置存储参数

在`SetStoreParams`存档中存储大量`CObject`派生对象时使用。

```
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>参数

*n哈希*<br/>
接口指针映射的哈希表的大小。 应为质数。

*nBlockSize*<br/>
指定用于扩展参数的内存分配粒度。 应该是一个功率2的最佳性能。

### <a name="remarks"></a>备注

`SetStoreParams`允许您设置哈希表大小和映射的块大小，用于在序列化过程中标识唯一对象。

在存储任何对象`SetStoreParams`或调用 MapObject 或[WriteObject](#mapobject) [WriteObject](#writeobject)之后，不得调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>C存档：写入

将指定数量的字节写入存档。

```
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向用户提供的缓冲区的指针，其中包含要写入存档的数据。

*nMax*<br/>
指定要写入存档的字节数的整数。

### <a name="remarks"></a>备注

存档不格式化字节。

可以使用`Write``Serialize`函数中的成员函数编写包含在对象中的普通结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>C存档：写入类

用于`WriteClass`在派生类的序列化期间存储基类的版本和类信息。

```
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>参数

*pClassRef*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针，对应于请求的类引用。

### <a name="remarks"></a>备注

`WriteClass`将基类的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的引用写入 。 `CArchive` 使用[CArchive：：读取类](#readclass)来检索引用。

`WriteClass`验证存档的类信息是否与运行时类兼容。 如果它不兼容，`WriteClass`将抛出一个[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

您的运行时类必须使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否则，`WriteClass`将抛出[一个CNot被支持例外](../../mfc/reference/cnotsupportedexception-class.md)。

可以使用[序列化类](#serializeclass)而不是`WriteClass`，来处理类引用的读取和写入。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>C存档：写入对象

将指定的`CObject`内容存储到存档。

```
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>参数

*Pob*<br/>
指向要存储的对象的常量指针。

### <a name="remarks"></a>备注

此函数通常由 的`CArchive`插入 （ **<<**） 运算符重`CObject`载调用。 `WriteObject`，反过来，`Serialize`调用存档的类的功能。

您必须使用IMPLEMENT_SERIAL宏来启用存档。 `WriteObject`将 ASCII 类名称写入存档。 此类名称稍后在加载过程中验证。 特殊的编码方案可防止类的多个对象的类名称不必要地重复。 此方案还防止冗余存储作为多个指针目标的对象。

确切的对象编码方法（包括 ASCII 类名称的存在）是一个实现详细信息，并可能在库的未来版本中更改。

> [!NOTE]
> 在开始存档所有对象之前，请完成创建、删除和更新它们。 如果将存档与对象修改混合在一起，您的存档将损坏。

### <a name="example"></a>示例

有关类`CAge`的定义，请参阅[CObList：：CObList 的示例](../../mfc/reference/coblist-class.md#coblist)。

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>C存档：：写入字符串

使用此成员函数将数据从缓冲区写入与`CArchive`对象关联的文件。

```
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向包含 null 终止文本字符串的缓冲区的指针。

### <a name="remarks"></a>备注

终止 null 字符 （"\0"） 不会写入文件;因此，不写入文件。也不是自动写入的新增文字。

`WriteString`引发一个异常以响应多个条件，包括磁盘满型条件。

`Write`也可用，但它不是终止 null 字符，而是将请求的字节数写入文件。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)<br/>
[套接字文件类](../../mfc/reference/csocketfile-class.md)
