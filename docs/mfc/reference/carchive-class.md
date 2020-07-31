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
ms.openlocfilehash: 48ed2a0edfcc17603a62e6830bf1c8d68c11932a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231892"
---
# <a name="carchive-class"></a>CArchive 类

允许你以永久二进制格式（通常为磁盘存储）保存对象的复杂网络，这些对象在删除这些对象后仍然存在。

## <a name="syntax"></a>语法

```
class CArchive
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CArchive：： CArchive](#carchive)|创建一个 `CArchive` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CArchive：： Abort](#abort)|关闭存档而不引发异常。|
|[CArchive：： Close](#close)|刷新未写入数据并断开与的连接 `CFile` 。|
|[CArchive：： Flush](#flush)|刷新存档缓冲区中的未写入数据。|
|[CArchive：： GetFile](#getfile)|获取 `CFile` 此存档的对象指针。|
|[CArchive：： GetObjectSchema](#getobjectschema)|从函数调用 `Serialize` ，以确定要反序列化的对象的版本。|
|[CArchive：： IsBufferEmpty](#isbufferempty)|确定在 Windows 套接接收过程中缓冲区是否已清空。|
|[CArchive：： IsLoading](#isloading)|确定存档是否正在加载。|
|[CArchive：： IsStoring](#isstoring)|确定存档是否正在存储。|
|[CArchive：： MapObject](#mapobject)|将不序列化的对象放置在映射中，但可供子对象引用的对象使用。|
|[CArchive：： Read](#read)|读取原始字节。|
|[CArchive：： ReadClass](#readclass)|读取以前用存储的类引用 `WriteClass` 。|
|[CArchive：： ReadObject](#readobject)|调用对象的 `Serialize` 函数以进行加载。|
|[CArchive：： ReadString](#readstring)|读取一行文本。|
|[CArchive：： SerializeClass](#serializeclass)|读取或写入对象的类引用， `CArchive` 具体取决于的方向 `CArchive` 。|
|[CArchive：： SetLoadParams](#setloadparams)|设置负载阵列增长到的大小。 在加载任何对象之前或在调用之前，必须先调用 `MapObject` `ReadObject` 。|
|[CArchive：： SetObjectSchema](#setobjectschema)|设置存储在 archive 对象中的对象架构。|
|[CArchive：： SetStoreParams](#setstoreparams)|设置在序列化过程中用于标识唯一对象的哈希表大小和块的块大小。|
|[CArchive：： Write](#write)|写入原始字节。|
|[CArchive：： WriteClass](#writeclass)|向写入对的引用 `CRuntimeClass` `CArchive` 。|
|[CArchive：： WriteObject](#writeobject)|为存储调用对象的 `Serialize` 函数。|
|[CArchive：： WriteString](#writestring)|写入一行文本。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CArchive：： operator&lt;&lt;](#operator_lt_lt)|将对象和基元类型存储到存档中。|
|[CArchive：： operator&gt;&gt;](#operator_gt_gt)|从存档中加载对象和基元类型。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CArchive：： m_pDocument](#m_pdocument)||

## <a name="remarks"></a>备注

`CArchive`没有基类。

稍后，你可以从持久性存储中加载对象，并在内存中重组它们。 使数据持久的这一过程称为 "序列化"。

可以将存档对象视为一种二进制流。 与输入/输出流一样，存档与文件相关联，并允许对存储的数据进行缓冲写入和读取。 输入/输出流处理 ASCII 字符的序列，而存档处理二进制对象数据，采用高效的 nonredundant 格式。

必须先创建一个[CFile](../../mfc/reference/cfile-class.md)对象，然后才能创建 `CArchive` 对象。 此外，必须确保存档的负载/存储状态与文件的打开模式兼容。 每个文件只能有一个活动存档。

构造 `CArchive` 对象时，可以将其附加到 `CFile` 表示打开的文件的类（或派生类）的对象。 你还可以指定是否将存档用于加载或存储。 `CArchive`对象不仅可处理基元类型，还可以处理为序列化而设计的[CObject](../../mfc/reference/cobject-class.md)派生类的对象。 可序列化的类通常具有 `Serialize` 成员函数，并且通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，如类中所述 `CObject` 。

重载的析取（ **>>** ）和插入（ **<<** ）运算符是支持基元类型和派生类的方便的存档编程接口 `CObject` 。

`CArchive`还支持通过 MFC Windows 套接类[CSocket](../../mfc/reference/csocket-class.md)和[CSocketFile](../../mfc/reference/csocketfile-class.md)进行编程。 [IsBufferEmpty](#isbufferempty)成员函数支持这种用法。

有关的详细信息 `CArchive` ，请参阅文章[序列化](../../mfc/serialization-in-mfc.md)和[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CArchive`

## <a name="requirements"></a>要求

**标头：** afx

## <a name="carchiveabort"></a><a name="abort"></a>CArchive：： Abort

调用此函数可关闭存档，而不引发异常。

```cpp
void Abort ();
```

### <a name="remarks"></a>备注

`CArchive`析构函数通常会调用 `Close` ，这会刷新尚未保存到关联对象的任何数据 `CFile` 。 这会导致异常。

捕获这些异常时，使用是一个不错的主意 `Abort` ，这样，destructing `CArchive` 对象不会导致异常。 在处理异常时， `CArchive::Abort` 将不会在失败时引发异常，因为与[CArchive：： Close](#close)不同，将 `Abort` 忽略失败。

如果使用在 **`new`** `CArchive` 堆上分配对象，则必须在关闭文件后将其删除。

### <a name="example"></a>示例

  请参阅[CArchive：： WriteClass](#writeclass)的示例。

## <a name="carchivecarchive"></a><a name="carchive"></a>CArchive：： CArchive

构造一个 `CArchive` 对象，并指定它是否将用于加载或存储对象。

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>参数

*.Pfile*<br/>
指向 `CFile` 对象的指针，该对象是持久性数据的最终源或目标。

*nMode*<br/>
一个标志，用于指定是从存档中加载对象还是将对象存储到存档中。 *NMode*参数必须具有以下值之一：

- `CArchive::load`从存档中加载数据。 只需要 " `CFile` 读取" 权限。

- `CArchive::store`将数据保存到存档。 需要 `CFile` 写入权限。

- `CArchive::bNoFlushOnDelete``Flush`当调用存档析构函数时，禁止存档自动调用。 如果设置此标志，则需要负责在 `Close` 调用析构函数之前显式调用。 否则，数据将会损坏。

*nBufSize*<br/>
一个整数，指定内部文件缓冲区的大小（以字节为单位）。 请注意，默认缓冲区大小为4096个字节。 如果你经常将大型对象存档，则如果你使用较大的缓冲区大小（这是文件缓冲区大小的倍数），将提高性能。

*lpBuf*<br/>
指向用户提供的大小*nBufSize*缓冲区的可选指针。 如果未指定此参数，则存档将从本地堆分配一个缓冲区，并在销毁对象时释放它。 存档不会释放用户提供的缓冲区。

### <a name="remarks"></a>备注

创建存档后，不能更改此规范。

在关闭存档之前，不能使用 `CFile` 操作来更改该文件的状态。 任何此类操作都会损坏存档的完整性。 可以在序列化过程中随时访问文件指针的位置，方法是从[GetFile](#getfile)成员函数获取存档文件对象，然后使用[CFile：： GetPosition](../../mfc/reference/cfile-class.md#getposition)函数。 在获取文件指针的位置之前，应调用[CArchive：： Flush](#flush) 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a>CArchive：： Close

刷新缓冲区中保留的所有数据，关闭存档，并将存档与文件断开连接。

```cpp
void Close();
```

### <a name="remarks"></a>备注

不允许对存档执行进一步的操作。 关闭存档后，可以为同一文件创建另一个存档，或者可以关闭该文件。

成员函数 `Close` 可确保将所有数据从存档传输到文件，并使存档不可用。 若要完成从文件到存储介质的传输，必须先使用[CFile：： Close](../../mfc/reference/cfile-class.md#close) ，然后销毁 `CFile` 对象。

### <a name="example"></a>示例

  请参阅[CArchive：： WriteString](#writestring)的示例。

## <a name="carchiveflush"></a><a name="flush"></a>CArchive：： Flush

强制将存档缓冲区中保留的所有数据写入文件。

```cpp
void Flush();
```

### <a name="remarks"></a>备注

成员函数 `Flush` 可确保将所有数据从存档传输到文件。 必须调用[CFile：： Close](../../mfc/reference/cfile-class.md#close)才能完成从文件到存储介质的传输。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a>CArchive：： GetFile

获取 `CFile` 此存档的对象指针。

```
CFile* GetFile() const;
```

### <a name="return-value"></a>返回值

指向正在使用的对象的常量指针 `CFile` 。

### <a name="remarks"></a>备注

使用之前，必须刷新存档 `GetFile` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a>CArchive：： GetObjectSchema

从函数中调用此函数 `Serialize` 可确定当前正在反序列化的对象的版本。

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>返回值

在反序列化期间，要读取的对象的版本。

### <a name="remarks"></a>备注

仅当 `CArchive` 加载对象（ [CArchive：： IsLoading](#isloading)返回非零）时，调用此函数才有效。 它应该是函数中的第一个调用 `Serialize` ，只调用一次。 （UINT）的返回值-1 指示版本号未知。

`CObject`派生类可以使用与架构版本本身（使用按位**或**）组合的 VERSIONABLE_SCHEMA （在 IMPLEMENT_SERIAL 宏中）来创建 "无版本冲突对象"，即，其 `Serialize` 成员函数可以读取多个版本的对象。 如果版本不匹配，则默认框架功能（无 VERSIONABLE_SCHEMA）会引发异常。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a>CArchive：： IsBufferEmpty

调用此成员函数以确定存档对象的内部缓冲区是否为空。

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>返回值

如果存档缓冲区为空，则为非零值;否则为0。

### <a name="remarks"></a>备注

提供此函数是为了支持与 MFC Windows 套接类的编程 `CSocketFile` 。 不需要将其用于与对象关联的存档 `CFile` 。

使用 `IsBufferEmpty` 与对象关联的存档的原因 `CSocketFile` 是存档的缓冲区可能包含多个消息或记录。 收到一条消息后，您应该使用 `IsBufferEmpty` 来控制在缓冲区为空之前继续接收数据的循环。 有关详细信息，请参阅类的[接收](../../mfc/reference/casyncsocket-class.md#receive)成员函数 `CAsyncSocket` ，该类演示如何使用 `IsBufferEmpty` 。

有关详细信息，请参阅[Windows 套接字：对存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。

## <a name="carchiveisloading"></a><a name="isloading"></a>CArchive：： IsLoading

确定存档是否正在加载数据。

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>返回值

如果存档当前用于加载，则为非零值;否则为0。

### <a name="remarks"></a>备注

存档类的函数会调用此成员函数 `Serialize` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a>CArchive：： IsStoring

确定存档是否正在存储数据。

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>返回值

如果存档当前用于存储，则为非零值;否则为0。

### <a name="remarks"></a>备注

存档类的函数会调用此成员函数 `Serialize` 。

如果 `IsStoring` 存档的状态为非零，则其 `IsLoading` 状态为0，反之亦然。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a>CArchive：： MapObject

调用此成员函数可将对象放入未真正序列化到文件中的对象，但可供子对象引用。

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>参数

*pOb*<br/>
指向要存储的对象的常量指针。

### <a name="remarks"></a>备注

例如，你可能不会序列化文档，但会序列化文档中的项。 通过调用 `MapObject` ，你可以允许这些项或子对象引用文档。 此外，序列化子项还可以序列化其*m_pDocument*后向指针。

`MapObject`当你在对象中存储和加载时，你可以调用 `CArchive` 。 `MapObject`在序列化和反序列化期间，将指定的对象添加到由对象维护的内部数据结构中 `CArchive` ，但与[ReadObject](#readobject)和[WriteObject](#writeobject)不同，它不会对对象调用序列化。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a>CArchive：： m_pDocument

设置为 NULL 默认情况下，指向的指针 `CDocument` 可设置为该实例的用户所需的任何内容 `CArchive` 。

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>备注

此指针的常见用法是将有关序列化过程的其他信息传递到要序列化的所有对象。 这是通过使用正在序列化的文档（派生类）初始化指针来实现的 `CDocument` ，在这种情况下，文档中的对象可以访问文档（如有必要）。 序列化期间，对象也使用此指针 `COleClientItem` 。

当用户发出文件打开或保存命令时，框架会将*m_pDocument*设置为要序列化的文档。 如果序列化对象链接和嵌入（OLE）容器文档，而不是打开或保存文件，则必须显式设置*m_pDocument*。 例如，在将容器文档序列化到剪贴板时，可以执行此操作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a>CArchive：： operator&lt;&lt;

将所指示的对象或基元类型存储到存档中。

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

一个 `CArchive` 引用，该引用在一行上启用多个插入运算符。

### <a name="remarks"></a>备注

上述两个版本专用于存储64位整数。

如果在类实现中使用 IMPLEMENT_SERIAL 宏，则为调用受保护的插入运算符 `CObject` `WriteObject` 。 此函数反过来调用 `Serialize` 类的函数。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入运算符（<<）支持诊断转储并存储到存档。

### <a name="example"></a>示例

此示例演示如何将 `CArchive` 插入运算符 << 与 **`int`** 和类型一起使用 **`long`** 。

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>示例

此示例2演示了如何将 `CArchive` 插入运算符与类型一起使用 << `CStringT` 。

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a>CArchive：： operator&gt;&gt;

从存档中加载指定的对象或基元类型。

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

一个 `CArchive` 引用，该引用在一行上启用多个提取运算符。

### <a name="remarks"></a>备注

上面的两个版本专用于加载64位整数。

如果在类实现中使用 IMPLEMENT_SERIAL 宏，则为 `CObject` 调用受保护 `ReadObject` 函数（使用非零运行时类指针）而重载的提取运算符。 此函数反过来调用 `Serialize` 类的函数。

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)提取运算符（>>）支持从存档进行加载。

### <a name="example"></a>示例

此示例演示如何将 `CArchive` 提取运算符与类型一起使用 >> **`int`** 。

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>示例

此示例演示如何将 `CArchive` 插入运算符和提取运算符 \< and > 与类型 <> 使用 `CStringT` 。

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a>CArchive：： Read

从存档中读取指定的字节数。

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向用户提供的用于接收从存档中读取的数据的缓冲区的指针。

*N 每天*<br/>
指定要从存档中读取的字节数的无符号整数。

### <a name="return-value"></a>返回值

包含实际读取的字节数的无符号整数。 如果返回值小于请求的数目，则已到达文件结尾。 文件尾条件不会引发异常。

### <a name="remarks"></a>备注

存档不会解释字节。

您可以使用 `Read` 函数中的成员函数 `Serialize` 来读取对象中包含的普通结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a>CArchive：： ReadClass

调用此成员函数以读取对先前存储在[WriteClass](#writeclass)中的类的引用。

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>参数

*pClassRefRequested*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针，该结构与请求的类引用相对应。 可以为 NULL。

*pSchema*<br/>
一个指针，指向以前存储的运行时类的架构。

*pObTag*<br/>
一个数字，表示对象的唯一标记。 由[ReadObject](#readobject)的实现在内部使用。 仅针对高级编程公开;*pObTag*通常应为 NULL。

### <a name="return-value"></a>返回值

指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针。

### <a name="remarks"></a>备注

如果*pClassRefRequested*不为 NULL，则 `ReadClass` 验证存档类信息是否与运行时类兼容。 如果不兼容， `ReadClass` 则将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

运行时类必须使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否则， `ReadClass` 将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

如果*pSchema*为 NULL，则可以通过调用[CArchive：： GetObjectSchema](#getobjectschema)来检索存储类的架构。否则， <strong>\*</strong> *pSchema*将包含以前存储的运行时类的架构。

您可以使用[SerializeClass](#serializeclass) （而不是 `ReadClass` ）来处理类引用的读取和写入。

### <a name="example"></a>示例

  请参阅[CArchive：： WriteClass](#writeclass)的示例。

## <a name="carchivereadobject"></a><a name="readobject"></a>CArchive：： ReadObject

从存档中读取对象数据，并构造适当类型的对象。

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>参数

*pClass*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的常量指针，该结构对应于要读取的对象。

### <a name="return-value"></a>返回值

必须使用[cobject：： IsKindOf](../../mfc/reference/cobject-class.md#iskindof)安全地强制转换为正确的派生类的[CObject](../../mfc/reference/cobject-class.md)指针。

### <a name="remarks"></a>备注

此函数通常由 `CArchive` **>>** [CObject](../../mfc/reference/cobject-class.md)指针的重载（）运算符调用。 `ReadObject`反过来，会调用 `Serialize` 存档类的函数。

如果提供一个非零*pClass*参数，该参数是由[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏获取的，则该函数将验证存档对象的运行时类。 这假定你已在类的实现中使用了 IMPLEMENT_SERIAL 宏。

### <a name="example"></a>示例

  请参阅[CArchive：： WriteObject](#writeobject)的示例。

## <a name="carchivereadstring"></a><a name="readstring"></a>CArchive：： ReadString

调用此成员函数以从与对象关联的文件中将文本数据读入缓冲区 `CArchive` 。

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>参数

*rString*<br/>
对[CString](../../atl-mfc-shared/reference/cstringt-class.md)的引用，在从与 CArchive 对象关联的文件中读取结果字符串后将包含该字符串。

*lpsz*<br/>
指定指向用户提供的缓冲区的指针，该缓冲区将接收以 null 结尾的文本字符串。

*N 每天*<br/>
指定要读取的最大字符数。 应小于*lpsz*缓冲区的大小。

### <a name="return-value"></a>返回值

在返回 BOOL 的版本中，如果成功，则为 TRUE;否则为 FALSE。

在返回的版本中 `LPTSTR` ，指向包含文本数据的缓冲区的指针;如果已到达文件末尾，则为 NULL。

### <a name="remarks"></a>备注

在具有*n 每天*参数的成员函数版本中，缓冲区最多可包含*n 每天*个字符的限制。 读取由回车换行符对停止。 尾随换行符始终会被删除。 在任一情况下，均追加一个 null 字符（' \ 0 '）。

[CArchive：： Read](#read)也可用于文本模式输入，但它不会在回车换行符对上终止。

### <a name="example"></a>示例

  请参阅[CArchive：： WriteString](#writestring)的示例。

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a>CArchive：： SerializeClass

如果要存储和加载基类的版本信息，请调用此成员函数。

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>参数

*pClassRef*<br/>
指向基类的运行时类对象的指针。

### <a name="remarks"></a>备注

`SerializeClass`根据的方向，将对类的引用读写到 `CArchive` 对象 `CArchive` 。 使用 `SerializeClass` 替代[ReadClass](#readclass)和[WriteClass](#writeclass)作为序列化基类对象的一种简便方法; `SerializeClass` 需要较少的代码和更少的参数。

与类似 `ReadClass` ， `SerializeClass` 验证存档类信息是否与运行时类兼容。 如果不兼容， `SerializeClass` 则将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

运行时类必须使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否则， `SerializeClass` 将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏检索*pRuntimeClass*参数的值。 基类必须使用[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a>CArchive：： SetLoadParams

`SetLoadParams` `CObject` 从存档中读取大量派生对象时调用。

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>参数

*nGrowBy*<br/>
如果需要增加大小，要分配的元素槽的最小数目。

### <a name="remarks"></a>备注

`CArchive`使用加载数组来解析对存储在存档中的对象的引用。 `SetLoadParams`允许设置负载阵列增长到的大小。

在 `SetLoadParams` 加载任何对象之后，或在调用[MapObject](#mapobject)或[ReadObject](#readobject)后，不能调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a>CArchive：： SetObjectSchema

调用此成员函数可将存档对象中存储的对象架构设置为*nSchema*。

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>参数

*nSchema*<br/>
指定对象的架构。

### <a name="remarks"></a>备注

对[GetObjectSchema](#getobjectschema)的下一次调用将返回存储在*nSchema*中的值。

用于 `SetObjectSchema` 高级版本控制; 例如，当你想要强制在派生类的函数中读取特定版本时 `Serialize` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a>CArchive：： SetStoreParams

`SetStoreParams` `CObject` 在存档中存储大量派生对象时使用。

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>参数

*nHashSize*<br/>
接口指针映射的哈希表的大小。 应为质数。

*nBlockSize*<br/>
指定用于扩展参数的内存分配粒度。 应为2的幂，以获得最佳性能。

### <a name="remarks"></a>备注

`SetStoreParams`允许您在序列化过程中设置用于标识唯一对象的哈希表大小和块的块大小。

在 `SetStoreParams` 存储任何对象之后，或在调用[MapObject](#mapobject)或[WriteObject](#writeobject)后，不能调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a>CArchive：： Write

向存档写入指定的字节数。

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>参数

*lpBuf*<br/>
指向用户提供的缓冲区的指针，该缓冲区包含要写入存档的数据。

*N 每天*<br/>
一个整数，指定要写入存档的字节数。

### <a name="remarks"></a>备注

存档不会格式化字节。

您可以使用 `Write` 函数中的成员函数 `Serialize` 来编写对象中包含的普通结构。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a>CArchive：： WriteClass

用于 `WriteClass` 在派生类的序列化过程中存储基类的版本和类信息。

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>参数

*pClassRef*<br/>
指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构的指针，该结构与请求的类引用相对应。

### <a name="remarks"></a>备注

`WriteClass`将基类的引用写入到的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) `CArchive` 。 请使用[CArchive：： ReadClass](#readclass)检索引用。

`WriteClass`验证存档类信息是否与运行时类兼容。 如果不兼容， `WriteClass` 则将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。

运行时类必须使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial);否则， `WriteClass` 将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。

您可以使用[SerializeClass](#serializeclass) （而不是 `WriteClass` ）来处理类引用的读取和写入。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a>CArchive：： WriteObject

将指定的存储 `CObject` 到存档中。

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>参数

*pOb*<br/>
指向要存储的对象的常量指针。

### <a name="remarks"></a>备注

此函数通常由 `CArchive` 为重载的插入（ **<<** ）运算符调用 `CObject` 。 `WriteObject`反过来，会调用 `Serialize` 存档类的函数。

必须使用 IMPLEMENT_SERIAL 宏来启用存档。 `WriteObject`将 ASCII 类名写入存档。 此类名称稍后会在加载过程中进行验证。 特殊编码方案可防止类的多个对象的类名重复。 此方案还可防止对多个指针的目标的对象进行冗余存储。

确切的对象编码方法（包括 ASCII 类名称）是实现详细信息，并且可能会在将来版本的库中更改。

> [!NOTE]
> 开始存档之前，请完成创建、删除和更新所有对象的操作。 如果将存档与对象修改混合使用，存档将会损坏。

### <a name="example"></a>示例

有关类的定义 `CAge` ，请参阅[CObList：： CObList](../../mfc/reference/coblist-class.md#coblist)的示例。

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a>CArchive：： WriteString

使用此成员函数将缓冲区中的数据写入与对象关联的文件 `CArchive` 。

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>参数

*lpsz*<br/>
指定指向包含以 null 结尾的文本字符串的缓冲区的指针。

### <a name="remarks"></a>备注

终止的 null 字符（"\ 0"）未写入文件;也不会自动写入一个换行符。

`WriteString`引发了一个异常，以响应多个条件，包括磁盘-全部条件。

`Write`还可用，但不会在 null 字符上终止，它将请求的字节数写入到文件中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>另请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CFile 类](../../mfc/reference/cfile-class.md)<br/>
[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[CSocket 类](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 类](../../mfc/reference/csocketfile-class.md)
