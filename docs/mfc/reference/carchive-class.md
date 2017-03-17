---
title: "CArchive 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- I/O [MFC], archiving objects
- CArchive class
- serialization [C++], CArchive class
- storage [C++], CArchive class
- data storage [C++], CArchive class
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 501b365678a45148aabe638ff341f3ae995e4ab5
ms.lasthandoff: 02/24/2017

---
# <a name="carchive-class"></a>CArchive 类
允许您保存复杂的对象网络以永久二进制格式 （通常为磁盘存储） 在这些对象删除后仍然存在。  
  
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
  
|名称|说明|  
|----------|-----------------|  
|[CArchive::Abort](#abort)|不引发任何异常关闭存档。|  
|[CArchive::Close](#close)|刷新未写入的数据，然后断开`CFile`。|  
|[CArchive::Flush](#flush)|从存档缓冲区刷新未写入的数据。|  
|[CArchive::GetFile](#getfile)|获取`CFile`该存档文件的对象指针。|  
|[CArchive::GetObjectSchema](#getobjectschema)|从调用`Serialize`函数来确定要反序列化的对象的版本。|  
|[CArchive::IsBufferEmpty](#isbufferempty)|确定是否已在 Windows 套接字清空缓冲区接收进程。|  
|[CArchive::IsLoading](#isloading)|确定是否正在加载存档。|  
|[CArchive::IsStoring](#isstoring)|确定是否存储存档。|  
|[CArchive::MapObject](#mapobject)|将对象放在映射中，不序列化到文件中，但可用于子对象来引用。|  
|[Carchive:: Read](#read)|读取原始字节。|  
|[CArchive::ReadClass](#readclass)|读取使用以前存储的类引用`WriteClass`。|  
|[CArchive::ReadObject](#readobject)|调用对象的`Serialize`加载的函数。|  
|[CArchive::ReadString](#readstring)|读取单个文本行。|  
|[CArchive::SerializeClass](#serializeclass)|读取或写入对类引用`CArchive`对象根据不同的方向`CArchive`。|  
|[CArchive::SetLoadParams](#setloadparams)|设置负载数组增长的大小。 加载的任何对象之前或之前必须调用`MapObject`或`ReadObject`调用。|  
|[CArchive::SetObjectSchema](#setobjectschema)|设置存储在存档对象中的对象架构。|  
|[CArchive::SetStoreParams](#setstoreparams)|设置哈希表大小和用于在序列化过程中标识唯一对象的映射的块大小。|  
|[Carchive:: Write](#write)|写入原始字节。|  
|[CArchive::WriteClass](#writeclass)|将引用写入`CRuntimeClass`到`CArchive`。|  
|[CArchive::WriteObject](#writeobject)|调用对象的`Serialize`用于存储的函数。|  
|[CArchive::WriteString](#writestring)|写入单个文本行。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[CArchive::operator&lt;&lt;](#operator_lt_lt)|将对象和基元类型到存档存储。|  
|[CArchive::operator&gt;&gt;](#operator_gt_gt)|从存档中加载对象和基元类型。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CArchive::m_pDocument](#m_pdocument)||  
  
## <a name="remarks"></a>备注  
 `CArchive`没有基类的类。  
  
 以后您可以从持久性存储区，将其重建在内存中加载的对象。 使数据持久性的这个过程称为"序列化。"  
  
 您可以将存档对象作为一种二进制流。 输入/输出流，如存档与文件相关联，并允许的缓冲的写入和读取到和从存储的数据。 输入/输出流处理 ASCII 字符的序列，但存档处理高效、 非冗余格式的二进制对象数据。  
  
 您必须创建[CFile](../../mfc/reference/cfile-class.md)对象，然后您可以创建`CArchive`对象。 此外，您必须确保存档的负载/存储区状态符合文件的打开模式。 则被限制到每个文件的一个活动存档。  
  
 当构造`CArchive`对象时，将其附加到类的对象`CFile`（或派生的类），表示打开的文件。 您还指定是否将用于加载或存储使用存档。 一个`CArchive`基元类型不仅的对象，对象可以处理[CObject](../../mfc/reference/cobject-class.md)-派生的类用于序列化。 可序列化的类通常具有`Serialize`成员函数，而且它通常使用[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，如类下所述`CObject`。  
  
 重载的提取 ( ** >> **) 和插入 ( ** << **) 运算符都是支持这两种基元类型的方便访问的存档编程接口和`CObject`的派生类。  
  
 `CArchive`此外支持使用 MFC Windows 套接字类编程[CSocket](../../mfc/reference/csocket-class.md)和[CSocketFile](../../mfc/reference/csocketfile-class.md)。 [IsBufferEmpty](#isbufferempty)成员函数支持该用法。  
  
 有关详细信息`CArchive`，请参阅文章[序列化](../../mfc/serialization-in-mfc.md)和[Windows 套接字︰ 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CArchive`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="abort"></a>CArchive::Abort  
 调用此函数不引发异常的情况下关闭存档。  
  
```  
void Abort ();
```  
  
### <a name="remarks"></a>备注  
 **CArchive**析构函数通常会调用**关闭**，这将刷新不保存任何数据到关联`CFile`对象。 这会导致异常。  
  
 当捕获这些异常，最好使用**中止**，因此析构`CArchive`对象不会产生其他异常。 当处理异常、`CArchive::Abort`不会引发异常有关失败原因，但不同[CArchive::Close](#close)，**中止**忽略失败。  
  
 如果您使用**新**分配`CArchive`对象在堆中，则必须关闭文件后删除它。  
  
### <a name="example"></a>示例  
  请参阅示例[CArchive::WriteClass](#writeclass)。  
  
##  <a name="carchive"></a>CArchive::CArchive  
 构造`CArchive`对象，并指定是否可利用它来加载或存储对象。  
  
```  
CArchive(
    CFile* pFile,  
    UINT nMode,  
    int nBufSize = 4096,  
    void* lpBuf = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pFile`  
 一个指向`CFile`的最终源或目标的持久性数据的对象。  
  
 `nMode`  
 一个标志，指定是否将从加载或存储到存档对象。 `nMode`参数都必须具有下列值之一︰  
  
- **CArchive::load**从存档中加载数据。 只要求`CFile`读取权限。  
  
- **CArchive::store**将数据保存到存档。 需要`CFile`写入权限。  
  
- **CArchive::bNoFlushOnDelete**自动调用阻止存档`Flush`存档析构函数调用时。 如果设置此标志，您负责进行显式调用**关闭**析构函数调用之前。 如果不这样做，将损坏您的数据。  
  
 `nBufSize`  
 一个整数，指定缓冲区大小的内部文件，以字节为单位。 请注意默认缓冲区大小为 4096 字节。 如果您定期存档大型对象，请将提高性能，如果您使用的文件的缓冲区大小的倍数的较大缓冲区大小。  
  
 `lpBuf`  
 指向用户提供的缓冲区大小的可选指针`nBufSize`。 如果不指定此参数，存档分配一个从本地堆的缓冲区，并将其释放时销毁该对象。 存档不会释放用户提供的缓冲区。  
  
### <a name="remarks"></a>备注  
 在创建存档后，您不能更改此规范。  
  
 不能使用`CFile`操作来更改该文件的状态，直到您关闭存档为止。 此类操作将存档的完整性造成破坏。 可以随时在序列化过程中访问的文件指针的位置通过获取从存档的文件对象[GetFile](#getfile)成员函数，然后使用[CFile::GetPosition](../../mfc/reference/cfile-class.md#getposition)函数。 应调用[CArchive::Flush](#flush)之前获取的文件指针的位置。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&12;](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]  
  
##  <a name="close"></a>CArchive::Close  
 将保留在缓冲区中的任何数据刷新，关闭存档，并断开与该文件的存档。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>备注  
 不允许在存档任何进一步的操作。 关闭存档后，您可以创建另一个存档的同一个文件，或者您可以关闭该文件。  
  
 成员函数**关闭**可确保所有数据都传输从存档到文件，并使存档不可用。 若要完成从文件传输到存储介质，必须首先使用[CFile::Close](../../mfc/reference/cfile-class.md#close)然后销毁`CFile`对象。  
  
### <a name="example"></a>示例  
  请参阅示例[CArchive::WriteString](#writestring)。  
  
##  <a name="flush"></a>CArchive::Flush  
 强制写入到文件的存档缓冲区中剩余的所有数据。  
  
```  
void Flush();
```  
  
### <a name="remarks"></a>备注  
 成员函数`Flush`可确保所有数据将从存档都传输到该文件。 必须调用[CFile::Close](../../mfc/reference/cfile-class.md#close)来完成从文件传输到存储介质。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&13;](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]  
  
##  <a name="getfile"></a>CArchive::GetFile  
 获取`CFile`该存档文件的对象指针。  
  
```  
CFile* GetFile() const;  
```  
  
### <a name="return-value"></a>返回值  
 常量指针的`CFile`中使用的对象。  
  
### <a name="remarks"></a>备注  
 您必须刷新在使用之前存档`GetFile`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&14;](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]  
  
##  <a name="getobjectschema"></a>CArchive::GetObjectSchema  
 调用此函数从`Serialize`函数来确定当前反序列化的对象的版本。  
  
```  
UINT GetObjectSchema();
```  
  
### <a name="return-value"></a>返回值  
 在反序列化，正在读取的对象的版本。  
  
### <a name="remarks"></a>备注  
 调用此函数时，才有效`CArchive`正在加载对象 ( [CArchive::IsLoading](#isloading)返回非零值)。 它应该是中的第一个调用`Serialize`函数并调用仅执行一次。 返回值 ( **UINT**) –&1; 指示的版本号为未知。  
  
 A `CObject`-派生的类可以使用**VERSIONABLE_SCHEMA**结合使用 (使用按位`OR`) 本身的架构版本 (在`IMPLEMENT_SERIAL`宏) 来创建一个"无版本冲突对象，对象"，它是一个对象其`Serialize`成员函数可以读取多个版本。 默认框架功能 (而无需**VERSIONABLE_SCHEMA**) 是版本不匹配时引发异常。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&15;](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]  
  
##  <a name="isbufferempty"></a>CArchive::IsBufferEmpty  
 调用该成员函数以确定是否存档对象的内部缓冲区为空。  
  
```  
BOOL IsBufferEmpty() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果存档的缓冲区为空，则为非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 此函数提供一个用于支持与 MFC Windows 套接字类编程`CSocketFile`。 不需要将其用于与相关联的存档`CFile`对象。  
  
 使用的原因`IsBufferEmpty`与存档与关联`CSocketFile`对象是︰ 对存档的缓冲区可能包含多个消息或记录。 在收到一条消息，应使用`IsBufferEmpty`来控制循环将继续接收数据，直到缓冲区为空。 有关详细信息，请参阅[接收](../../mfc/reference/casyncsocket-class.md#receive)类的成员函数`CAsyncSocket`，它显示如何使用`IsBufferEmpty`。  
  
 有关详细信息，请参阅[Windows 套接字︰ 使用存档使用套接字](../../mfc/windows-sockets-using-sockets-with-archives.md)。  
  
##  <a name="isloading"></a>CArchive::IsLoading  
 确定是否存档正在加载数据。  
  
```  
BOOL IsLoading() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果存档当前正用于加载; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 调用此成员函数`Serialize`存档类的函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&16;](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]  
  
##  <a name="isstoring"></a>CArchive::IsStoring  
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
 [!code-cpp[NVC_MFCSerialization #&17;](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]  
  
##  <a name="mapobject"></a>CArchive::MapObject  
 调用此成员函数以将对象放置在映射中，不会真正序列化到文件中，但可用于子对象来引用。  
  
```  
void MapObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>参数  
 `pOb`  
 指向要存储的对象的常量指针。  
  
### <a name="remarks"></a>备注  
 例如，您可能不序列化文档，但将序列化文档的一部分的项。 通过调用`MapObject`，可通过允许这些项或子对象引用的文档。 此外，序列化的子项可进行序列化其`m_pDocument`后向指针。  
  
 您可以调用`MapObject`时将存储到和从加载`CArchive`对象。 `MapObject`将指定的对象添加到由维护的内部数据结构`CArchive`对象序列化和反序列化过程中，但与不同[ReadObject](#readobject)和[WriteObject](#writeobject)**，**不会调用序列化的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&18;](../../mfc/codesnippet/cpp/carchive-class_7.h)]  
  
 [!code-cpp[NVC_MFCSerialization #&19;](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]  
  
 [!code-cpp[NVC_MFCSerialization #&20;](../../mfc/codesnippet/cpp/carchive-class_9.h)]  
  
 [!code-cpp[NVC_MFCSerialization #&21;](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]  
  
##  <a name="m_pdocument"></a>CArchive::m_pDocument  
 设置为**NULL**默认情况下，此指针**CDocument**可以设置为任何操作的用户`CArchive`实例的需要。  
  
```  
CDocument* m_pDocument;  
```  
  
### <a name="remarks"></a>备注  
 This 指针的常见用法是传达有关对正在序列化的所有对象的序列化过程的其他信息。 这通过初始化与该文档的指针 ( **CDocument**的派生类)，正在序列化，如有必要，在文档中的对象可以访问该文档的方式。 此指针也可由`COleClientItem`在序列化过程的对象。  
  
 框架集`m_pDocument`对文档进行序列化时用户发出一个文件打开或保存命令。 如果序列化文件打开或保存以外的原因的对象链接和嵌入 (OLE) 容器文档，您必须显式设置`m_pDocument`。 例如，在序列化到剪贴板容器文档时将执行此操作。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&35;](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]  
  
##  <a name="operator_lt_lt"></a>CArchive::operator&lt;&lt;  
 存储指定的对象或基元类型设置为存档。  
  
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
 一个`CArchive`使在单独的行的多个插入操作员的引用。  
  
### <a name="remarks"></a>备注  
 上面的最后两个版本是专用于存储 64 位整数。  
  
 如果您使用`IMPLEMENT_SERIAL`宏的类实现中，则为重载插入运算符`CObject`调用受保护**WriteObject**。 此函数反过来调用`Serialize`类函数。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)插入运算符 (<) supports diagnostic dumping and storing to an archive. supports="" diagnostic="" dumping="" and="" storing="" to="" an=""></) supports diagnostic dumping and storing to an archive.>  
  
### <a name="example"></a>示例  
 此示例演示如何使用`CArchive`插入运算符< with="" the="">`int`和`long`类型。  
  
 [!code-cpp[NVC_MFCSerialization #&31;](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]  
  
### <a name="example"></a>示例  
 此示例 2 演示如何使用`CArchive`插入运算符< with="" the="">`CStringT`类型。  
  
 [!code-cpp[NVC_MFCSerialization #&32;](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]  
  
##  <a name="operator_gt_gt"></a>CArchive::operator&gt;&gt;  
 从存档中加载的指定的对象或基元类型。  
  
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
 一个`CArchive`使多个提取操作员在单独的行的引用。  
  
### <a name="remarks"></a>备注  
 上面的最后两个版本是专门用于加载 64 位整数。  
  
 如果您使用`IMPLEMENT_SERIAL`宏的类实现中，则为重载提取运算符`CObject`调用受保护**ReadObject**函数 （非零的运行时类的指针）。 此函数反过来调用`Serialize`类函数。  
  
 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)提取运算符 (>) 支持从存档加载。  
  
### <a name="example"></a>示例  
 此示例演示如何使用`CArchive`提取运算符 >> 与`int`类型。  
  
 [!code-cpp[NVC_MFCSerialization 第&33;](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]  
  
### <a name="example"></a>示例  
 此示例演示如何使用`CArchive`插入和提取运算符\<和 >> 与`CStringT`类型。  
  
 [!code-cpp[NVC_MFCSerialization #&34;](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]  
  
##  <a name="read"></a>Carchive:: Read  
 从存档中读取指定的数目的字节。  
  
```  
UINT Read(void* lpBuf, UINT nMax);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 指向将接收从存档读取数据的用户提供的缓冲区的指针。  
  
 `nMax`  
 无符号的整数指定的字节数从存档读取。  
  
### <a name="return-value"></a>返回值  
 一个包含实际读取的字节数的无符号的整数。 如果返回的值小于请求的数目，已达到文件末尾。 不会引发异常的文件尾条件。  
  
### <a name="remarks"></a>备注  
 存档将字节不解释。  
  
 您可以使用**读取**成员函数内的您`Serialize`用于读取对象中包含的普通结构函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&24;](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]  
  
##  <a name="readclass"></a>CArchive::ReadClass  
 调用此成员函数可读取与以前存储在一个类的参考[WriteClass](#writeclass)。  
  
```  
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,  
    UINT* pSchema = NULL,  
    DWORD* pObTag = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pClassRefRequested`  
 一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构，它对应于请求了类引用。 可以是**NULL**。  
  
 `pSchema`  
 指向的架构是以前存储的运行时类的指针。  
  
 `pObTag`  
 对象的唯一标记是指一个数字。 供内部使用的实现[ReadObject](#readobject)。 公开的高级编程功能`pObTag`正常情况应**NULL**。  
  
### <a name="return-value"></a>返回值  
 一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 如果`pClassRefRequested`不是**NULL**，`ReadClass`验证是否已存档的类信息是否符合您的运行时类。 如果不兼容，`ReadClass`将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必须使用运行时类[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); 否则为`ReadClass`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 如果`pSchema`是**NULL**，来检索存储类的架构，只需调用[CArchive::GetObjectSchema](#getobjectschema); 否则为** \* ** `pSchema`将包含以前存储的运行时类的架构。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`ReadClass`，用于处理读取和写入类引用。  
  
### <a name="example"></a>示例  
  请参阅示例[CArchive::WriteClass](#writeclass)。  
  
##  <a name="readobject"></a>CArchive::ReadObject  
 从存档读取对象数据，并构造相应类型的对象。  
  
```  
CObject* ReadObject(const CRuntimeClass* pClass);
```  
  
### <a name="parameters"></a>参数  
 `pClass`  
 常量指针的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)对应于您希望读取的对象的结构。  
  
### <a name="return-value"></a>返回值  
 一个[CObject](../../mfc/reference/cobject-class.md)必须安全地转换为正确的指针使用派生类[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)。  
  
### <a name="remarks"></a>备注  
 通常情况下调用此函数`CArchive`提取 ( ** >> **) 的重载运算符[CObject](../../mfc/reference/cobject-class.md)指针。 **ReadObject**，反过来，调用`Serialize`存档类的函数。  
  
 如果您提供了非零`pClass`参数，它通过获取[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏，则函数将验证存档的对象的运行时类。 这里假定已使用`IMPLEMENT_SERIAL`类的实现中的宏。  
  
### <a name="example"></a>示例  
  请参阅示例[CArchive::WriteObject](#writeobject)。  
  
##  <a name="readstring"></a>CArchive::ReadString  
 调用此成员函数以文本数据读入的缓冲区与关联的文件从`CArchive`对象。  
  
```  
BOOL ReadString(CString& rString); 
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```  
  
### <a name="parameters"></a>参数  
 `rString`  
 对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)读取从与 CArchive 对象关联的文件后将包含生成的字符串。  
  
 `lpsz`  
 指定向用户提供将接收的以 null 结尾的文本字符串的缓冲区的指针。  
  
 `nMax`  
 指定的最大要读取的字符数。 应该发出一个大小小于*lpsz*缓冲区。  
  
### <a name="return-value"></a>返回值  
 返回的版本中**BOOL**， **TRUE**如果成功，则**FALSE**否则为。  
  
 返回的版本中`LPTSTR`，指向包含的文本数据; 的缓冲区的指针**NULL**如果已到达文件末尾。  
  
### <a name="remarks"></a>备注  
 成员函数时的版本中`nMax`参数，该缓冲区会保存最多的限制为`nMax`-1 个字符。 读取由回车-换行对已停止。 始终删除尾随新行字符。 在任一情况下将追加 null 字符 (\0)。  
  
 [Carchive:: Read](#read)也是可用的文本模式下输入，但它回车-换行对不会终止。  
  
### <a name="example"></a>示例  
  请参阅示例[CArchive::WriteString](#writestring)。  
  
##  <a name="serializeclass"></a>CArchive::SerializeClass  
 当您想要存储和加载的基类的版本信息时，请调用此成员函数。  
  
```  
void SerializeClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>参数  
 `pClassRef`  
 指向基类的运行时类对象的指针。  
  
### <a name="remarks"></a>备注  
 `SerializeClass`读取或写入到将类传递给引用`CArchive`对象，根据不同的方向`CArchive`。 使用`SerializeClass`代替了[ReadClass](#readclass)和[WriteClass](#writeclass)方便地进行序列化基类对象;`SerializeClass`要求更少的代码和较少的参数。  
  
 如`ReadClass`，`SerializeClass`验证是否已存档的类信息是否符合您的运行时类。 如果不兼容，`SerializeClass`将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必须使用运行时类[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); 否则为`SerializeClass`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 使用[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class)宏要检索的值为`pRuntimeClass`参数。 必须使用的基类[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&25;](../../mfc/codesnippet/cpp/carchive-class_17.h)]  
  
##  <a name="setloadparams"></a>CArchive::SetLoadParams  
 调用`SetLoadParams`时要读取的大量`CObject`-从存档派生的对象。  
  
```  
void SetLoadParams(UINT nGrowBy = 1024);
```  
  
### <a name="parameters"></a>参数  
 `nGrowBy`  
 要分配的大小增长是否需要的元素插槽最少次数。  
  
### <a name="remarks"></a>备注  
 `CArchive`使用负载数组来解析对存储在存档中的对象的引用。 `SetLoadParams`可以将负载数组增长的大小设置。  
  
 您不能调用`SetLoadParams`加载的任何对象之后，或在[MapObject](#mapobject)或[ReadObject](#readobject)调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&26;](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="setobjectschema"></a>CArchive::SetObjectSchema  
 调用此成员函数以设置存储在存档到对象中的对象架构`nSchema`。  
  
```  
void SetObjectSchema(UINT nSchema);
```  
  
### <a name="parameters"></a>参数  
 `nSchema`  
 指定对象的架构。  
  
### <a name="remarks"></a>备注  
 在下次调用[GetObjectSchema](#getobjectschema)将返回值存储在`nSchema`。  
  
 使用`SetObjectSchema`的高级版本控制功能; 例如，当你想要强制的特定版本中读入`Serialize`派生类的函数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&27;](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]  
  
##  <a name="setstoreparams"></a>CArchive::SetStoreParams  
 使用`SetStoreParams`存储的数量大时`CObject`-派生存档中的对象。  
  
```  
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```  
  
### <a name="parameters"></a>参数  
 *nHashSize*  
 将映射的接口指针的哈希表的大小。 应为质数。  
  
 `nBlockSize`  
 指定扩展参数的内存分配粒度。 应为获得最佳性能的 2 的幂。  
  
### <a name="remarks"></a>备注  
 `SetStoreParams`允许您设置哈希表大小和用于在序列化过程中标识唯一对象的映射的块大小。  
  
 您不能调用`SetStoreParams`存储的任何对象之后，或在[MapObject](#mapobject)或[WriteObject](#writeobject)调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&26;](../../mfc/codesnippet/cpp/carchive-class_18.h)]  
  
##  <a name="write"></a>Carchive:: Write  
 将指定的数目的字节写入存档。  
  
```  
void Write(const void* lpBuf, INT nMax);
```  
  
### <a name="parameters"></a>参数  
 `lpBuf`  
 指向包含要写入到存档的数据的用户提供的缓冲区的指针。  
  
 `nMax`  
 一个整数，指定要写入到存档的字节数。  
  
### <a name="remarks"></a>备注  
 存档不会格式化字节数。  
  
 您可以使用**编写**成员函数内的您`Serialize`函数可以编写普通结构包含在您的对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization 第&23;](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]  
  
##  <a name="writeclass"></a>CArchive::WriteClass  
 使用`WriteClass`来存储的版本和类信息的基类在派生类的序列化过程。  
  
```  
void WriteClass(const CRuntimeClass* pClassRef);
```  
  
### <a name="parameters"></a>参数  
 `pClassRef`  
 一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)结构，它对应于请求了类引用。  
  
### <a name="remarks"></a>备注  
 `WriteClass`将引用写入[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)到基类`CArchive`。 使用[CArchive::ReadClass](#readclass)以便检索的引用。  
  
 `WriteClass`验证已存档的类信息符合您的运行时类。 如果不兼容，`WriteClass`将引发[CArchiveException](../../mfc/reference/carchiveexception-class.md)。  
  
 必须使用运行时类[DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial)和[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial); 否则为`WriteClass`将引发[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 您可以使用[SerializeClass](#serializeclass)而不是`WriteClass`，用于处理读取和写入类引用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&28;](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]  
  
##  <a name="writeobject"></a>CArchive::WriteObject  
 将存储指定`CObject`到存档。  
  
```  
void WriteObject(const CObject* pOb);
```  
  
### <a name="parameters"></a>参数  
 `pOb`  
 指向要存储的对象的常量指针。  
  
### <a name="remarks"></a>备注  
 通常情况下调用此函数`CArchive`插入 ( ** << **) 的重载运算符`CObject`。 **WriteObject**，反过来，调用`Serialize`存档类的函数。  
  
 必须使用`IMPLEMENT_SERIAL`宏，以启用存档。 **WriteObject** ASCII 类名称写入存档。 此类名称会在加载过程中验证。 特殊的编码方案可防止不必要的类的多个对象的类名重复。 这种方案还可以防止冗余存储的目标的多个指针的对象。  
  
 确切编码方法 （包括存在 ASCII 类名称） 的对象是实现详细信息，并可以更改在将来版本的库。  
  
> [!NOTE]
>  创建、 删除和更新您的所有对象，将它们存档在开始之前完成。 如果混合使用归档与对象的修改会损坏您的存档。  
  
### <a name="example"></a>示例  
 有关的类定义`CAge`，请参阅示例[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)。  
  
 [!code-cpp[NVC_MFCSerialization #&29;](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]  
  
##  <a name="writestring"></a>CArchive::WriteString  
 使用此成员函数将数据从缓冲区写入到与关联的文件`CArchive`对象。  
  
```  
void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指定指向包含以 null 结尾的文本字符串的缓冲区的指针。  
  
### <a name="remarks"></a>备注  
 终止 null 字符 (\0') 不会写入该文件;也不新行自动写入。  
  
 `WriteString`对多个条件，包括磁盘已满条件的响应，则会引发异常。  
  
 **编写**也是可用，但它可以而不是终止 null 字符，来将该文件写入请求的字节数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCSerialization #&30;](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [CSocket 类](../../mfc/reference/csocket-class.md)   
 [CSocketFile 类](../../mfc/reference/csocketfile-class.md)

