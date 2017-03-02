---
title: "CFileFind 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileFind
dev_langs:
- C++
helpviewer_keywords:
- files [C++], finding
- Internet files [C++], finding
- CFileFind class
- URLs [C++], searching for
- local files
- local files, searching for
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
caps.latest.revision: 22
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
ms.openlocfilehash: d7e6500dfc0ff24f35dd021a54080eb7ba7f1655
ms.lasthandoff: 02/24/2017

---
# <a name="cfilefind-class"></a>CFileFind 类
执行本地文件搜索和是类的基类[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)，执行 Internet 文件搜索。  
  
## <a name="syntax"></a>语法  
  
```  
class CFileFind : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFileFind::CFileFind](#cfilefind)|构造 `CFileFind` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileFind::Close](#close)|关闭搜索请求。|  
|[CFileFind::FindFile](#findfile)|搜索指定的文件名称的目录。|  
|[CFileFind::FindNextFile](#findnextfile)|将继续从以前调用文件搜索[FindFile](#findfile)。|  
|[CFileFind::GetCreationTime](#getcreationtime)|获取创建文件时的时间。|  
|[CFileFind::GetFileName](#getfilename)|获取文件的名称，包括找到的文件的扩展名|  
|[CFileFind::GetFilePath](#getfilepath)|获取找到的文件的整个路径。|  
|[CFileFind::GetFileTitle](#getfiletitle)|获取找到的文件的标题。 标题不包含扩展名。|  
|[CFileFind::GetFileURL](#getfileurl)|获取包括的文件路径，找到的文件的 URL。|  
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|获取最后一次访问该文件的时间。|  
|[CFileFind::GetLastWriteTime](#getlastwritetime)|获取上次更改和保存该文件的时间。|  
|[CFileFind::GetLength](#getlength)|获取找到的文件，以字节为单位的长度。|  
|[CFileFind::GetRoot](#getroot)|获取找到的文件的根目录。|  
|[CFileFind::IsArchived](#isarchived)|确定是否存档找到的文件。|  
|[CFileFind::IsCompressed](#iscompressed)|确定是否找到的文件进行压缩。|  
|[CFileFind::IsDirectory](#isdirectory)|确定是否找到的文件是一个目录。|  
|[CFileFind::IsDots](#isdots)|确定是否找到文件的名称具有名称"。".."，该值指示实际上是一个目录。|  
|[CFileFind::IsHidden](#ishidden)|确定是否隐藏找到的文件。|  
|[CFileFind::IsNormal](#isnormal)|确定是否找到的文件是普通 （即，没有任何其他属性）。|  
|[CFileFind::IsReadOnly](#isreadonly)|确定是否找到的文件是只读的。|  
|[CFileFind::IsSystem](#issystem)|确定是否找到的文件系统文件。|  
|[CFileFind::IsTemporary](#istemporary)|确定是否临时找到的文件。|  
|[CFileFind::MatchesMask](#matchesmask)|指示要找的文件的所需的文件属性。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFileFind::CloseContext](#closecontext)|关闭当前搜索句柄指定的文件。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CFileFind::m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 对象的指针。|  
  
## <a name="remarks"></a>备注  
 `CFileFind`包含成员函数开始的搜索、 查找文件，并将返回标题、 名称或文件的路径。 对于 Internet 搜索，成员函数[GetFileURL](#getfileurl)返回文件的 URL。  
  
 `CFileFind`两个其他 MFC 类的基类设计为搜索特定服务器类型︰ `CGopherFileFind` gopher 服务器专门的合作和`CFtpFileFind`专门与 FTP 服务器的工作。 在一起，这三个类提供一种无缝机制以查找本地计算机或远程服务器上的文件，而不管服务器协议、 文件类型或位置，使客户端。  
  
 下面的代码将枚举当前目录中，打印的每个文件的名称中的所有文件︰  
  
 [!code-cpp[NVC_MFCFiles #&31;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]  
  
 为了使示例尽量简单，这段代码使用 c + + 标准库`cout`类。 `cout`行可以替换为调用`CListBox::AddString`，例如，在程序中使用图形用户界面。  
  
 有关如何使用`CFileFind`和其他 WinInet 类，请参阅文章[Internet 编程与 WinInet](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecfilefinda--cfilefindcfilefind"></a><a name="cfilefind"></a>CFileFind::CFileFind  
 当调用此成员函数`CFileFind`构造对象。  
  
```  
CFileFind();  
CFileFind(CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>参数  
 `pTM`  
 指向 CAtlTransactionManager 对象的指针  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="a-nameclosea--cfilefindclose"></a><a name="close"></a>CFileFind::Close  
 调用该成员函数以结束搜索、 重置上下文，并释放所有资源。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>备注  
 在调用**关闭**，不需要创建一个新`CFileFind`实例之前调用[FindFile](#findfile)若要开始新的搜索。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="a-nameclosecontexta--cfilefindclosecontext"></a><a name="closecontext"></a>CFileFind::CloseContext  
 关闭当前搜索句柄指定的文件。  
  
```  
virtual void CloseContext();
```  
  
### <a name="remarks"></a>备注  
 关闭搜索句柄的当前值来指定的文件。 重写此函数可更改默认行为。  
  
 必须调用[FindFile](#findfile)或[FindNextFile](#findnextfile)函数至少一次检索有效的搜索句柄。 **FindFile**和`FindNextFile`函数使用搜索句柄来找到具有给定名称匹配的名称的文件。  
  
##  <a name="a-namefindfilea--cfilefindfindfile"></a><a name="findfile"></a>CFileFind::FindFile  
 调用该成员函数以打开文件搜索。  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwUnused = 0);
```  
  
### <a name="parameters"></a>参数  
 `pstrName`  
 指向包含要查找的文件的名称的字符串的指针。 如果您通过**NULL**为`pstrName`， **FindFile**没有通配符 (*。\*) 搜索。  
  
 *dwUnused*  
 保留以使**FindFile**多态关系，派生类。 必须为 0。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 在调用**FindFile**若要开始搜索文件，请调用[FindNextFile](#findnextfile)检索后续文件。 必须调用`FindNextFile`以前至少一次调用任何以下特性的成员函数︰  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [IsNormal](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="a-namefindnextfilea--cfilefindfindnextfile"></a><a name="findnextfile"></a>CFileFind::FindNextFile  
 调用此成员函数，可继续从以前调用文件搜索[FindFile](#findfile)。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>返回值  
 非零，如果有多个文件;如果找到该文件是在目录中的最后一个，或者出现错误，则为零。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到该文件是在目录中，最后一个文件，或者如果没有匹配可以找到文件，`GetLastError`函数将返回 ERROR_NO_MORE_FILES。  
  
### <a name="remarks"></a>备注  
 必须调用`FindNextFile`以前至少一次调用任何以下特性的成员函数︰  
  
- [GetCreationTime](#getcreationtime)  
  
- [GetFileName](#getfilename)  
  
- [GetFileTitle](#getfiletitle)  
  
- [GetFilePath](#getfilepath)  
  
- [GetFileURL](#getfileurl)  
  
- [GetLastAccessTime](#getlastaccesstime)  
  
- [GetLastWriteTime](#getlastwritetime)  
  
- [GetLength](#getlength)  
  
- [GetRoot](#getroot)  
  
- [IsArchived](#isarchived)  
  
- [IsCompressed](#iscompressed)  
  
- [IsDirectory](#isdirectory)  
  
- [IsDots](#isdots)  
  
- [IsHidden](#ishidden)  
  
- [IsNormal](#isnormal)  
  
- [IsReadOnly](#isreadonly)  
  
- [IsSystem](#issystem)  
  
- [IsTemporary](#istemporary)  
  
- [MatchesMask](#matchesmask)  
  
 `FindNextFile`封装的 Win32 函数[FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428)。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="a-namegetcreationtimea--cfilefindgetcreationtime"></a><a name="getcreationtime"></a>CFileFind::GetCreationTime  
 调用此成员函数可获取指定的文件的创建的时间。  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `pTimeStamp`  
 一个指向[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含该文件的创建的时间。  
  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果不成功，则为 0。 `GetCreationTime`仅当将返回 0 [FindNextFile](#findnextfile)永远不会对此已调用`CFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetCreationTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可返回相同的函数所返回的其他时间戳如果基础文件系统或服务器不支持保留的时间属性的值。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 某些操作在系统上，返回的时间是在区域本地计算机到了该文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API 的详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-namegetfilenamea--cfilefindgetfilename"></a><a name="getfilename"></a>CFileFind::GetFileName  
 调用该成员函数以获取找到的文件的名称。  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>返回值  
 最近发现文件的名称。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)调用 GetFileName 之前至少一次。  
  
 `GetFileName`是一个包含三个`CFileFind`返回某种形式的文件名称的成员函数。 下面介绍了三个，它们会有所不同︰  
  
- `GetFileName`返回包含扩展名的文件名称。 例如，调用`GetFileName`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回文件名`myfile.txt`。  
  
- [GetFilePath](#getfilepath)返回该文件的完整路径。 例如，调用`GetFilePath`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回的文件路径`c:\myhtml\myfile.txt`。  
  
- [GetFileTitle](#getfiletitle)返回文件名称，而不包括文件扩展名。 例如，调用`GetFileTitle`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回文件标题`myfile`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&32;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]  
  
##  <a name="a-namegetfilepatha--cfilefindgetfilepath"></a><a name="getfilepath"></a>CFileFind::GetFilePath  
 调用该成员函数以获取指定的文件的完整路径。  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定文件的路径。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetFilePath`。  
  
 `GetFilePath`是一个包含三个`CFileFind`返回某种形式的文件名称的成员函数。 下面介绍了三个，它们会有所不同︰  
  
- [GetFileName](#getfilename)返回包括扩展名的文件名。 例如，调用`GetFileName`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回文件名`myfile.txt`。  
  
- `GetFilePath`返回该文件的完整路径。 例如，调用`GetFilePath`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回的文件路径`c:\myhtml\myfile.txt`。  
  
- [GetFileTitle](#getfiletitle)返回文件名称，而不包括文件扩展名。 例如，调用`GetFileTitle`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回文件标题`myfile`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="a-namegetfiletitlea--cfilefindgetfiletitle"></a><a name="getfiletitle"></a>CFileFind::GetFileTitle  
 调用此成员函数可获取找到的文件的标题。  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 该文件的标题。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetFileTitle`。  
  
 `GetFileTitle`是一个包含三个`CFileFind`返回某种形式的文件名称的成员函数。 下面介绍了三个，它们会有所不同︰  
  
- [GetFileName](#getfilename)返回包括扩展名的文件名。 例如，调用`GetFileName`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回文件名`myfile.txt`。  
  
- [GetFilePath](#getfilepath)返回该文件的完整路径。 例如，调用`GetFilePath`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回的文件路径`c:\myhtml\myfile.txt`。  
  
- `GetFileTitle`返回不包括文件扩展名的文件名称。 例如，调用`GetFileTitle`以生成有关文件的用户消息`c:\myhtml\myfile.txt`返回文件标题`myfile`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="a-namegetfileurla--cfilefindgetfileurl"></a><a name="getfileurl"></a>CFileFind::GetFileURL  
 调用此成员函数以检索指定的 URL。  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 完整的 URL。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetFileURL`。  
  
 `GetFileURL`类似于成员函数[GetFilePath](#getfilepath)，只不过它的形式返回 URL `file://path`。 例如，调用`GetFileURL`以获取有关的完整 URL`myfile.txt`返回的 URL `file://c:\myhtml\myfile.txt`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="a-namegetlastaccesstimea--cfilefindgetlastaccesstime"></a><a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime  
 调用此成员函数以获得上次访问指定的文件的时间。  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>参数  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
 `pTimeStamp`  
 一个指向[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含上一次访问该文件的时间。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果不成功，则为 0。 `GetLastAccessTime`仅当将返回 0 [FindNextFile](#findnextfile)永远不会对此已调用`CFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetLastAccessTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可返回相同的函数所返回的其他时间戳如果基础文件系统或服务器不支持保留的时间属性的值。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 某些操作在系统上，返回的时间是在区域本地计算机到了该文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API 的详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-namegetlastwritetimea--cfilefindgetlastwritetime"></a><a name="getlastwritetime"></a>CFileFind::GetLastWriteTime  
 调用此成员函数可获取上次更改该文件的时间。  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `pTimeStamp`  
 一个指向[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含上一次写入该文件的时间。  
  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值如果不成功，则为 0。 `GetLastWriteTime`仅当将返回 0 [FindNextFile](#findnextfile)永远不会对此已调用`CFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetLastWriteTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可返回相同的函数所返回的其他时间戳如果基础文件系统或服务器不支持保留的时间属性的值。 请参阅[Win32_Find_Data](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 某些操作在系统上，返回的时间是在区域本地计算机到了该文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API 的详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-namegetlengtha--cfilefindgetlength"></a><a name="getlength"></a>CFileFind::GetLength  
 调用该成员函数以获取找到的文件，以字节为单位的长度。  
  
```  
ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 找到的文件，以字节为单位的长度。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetLength`。  
  
 `GetLength`使用 Win32 结构[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)获取和返回值的文件的大小，以字节为单位。  
  
> [!NOTE]
>  从 MFC 7.0 起`GetLength`支持 64 位整数类型。 以前用此较新版本的库生成的现有代码可能会导致截断警告。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles 第&33;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]  
  
##  <a name="a-namegetroota--cfilefindgetroot"></a><a name="getroot"></a>CFileFind::GetRoot  
 调用此成员函数可获取找到的文件的根。  
  
```  
virtual CString GetRoot() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动搜索的根。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`GetRoot`。  
  
 此成员函数返回的驱动器名和路径名称用于开始搜索。 例如，调用[FindFile](#findfile)与`*.dat`导致`GetRoot`返回空字符串。 将传递一个路径，如`c:\windows\system\*.dll`到**FindFile**结果`GetRoot`返回`c:\windows\system\`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="a-nameisarchiveda--cfilefindisarchived"></a><a name="isarchived"></a>CFileFind::IsArchived  
 调用该成员函数以确定是否存档找到的文件。  
  
```  
BOOL IsArchived() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序将标记一个存档文件，它是备份或移除了 FILE_ATTRIBUTE_ARCHIVE，文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsArchived`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-nameiscompresseda--cfilefindiscompressed"></a><a name="iscompressed"></a>CFileFind::IsCompressed  
 调用该成员函数以确定是否找到的文件进行压缩。  
  
```  
BOOL IsCompressed() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 压缩的文件都标有 FILE_ATTRIBUTE_COMPRESSED、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 对于文件，此属性指示对所有文件中的数据进行压缩。 对于目录，此属性指示压缩为新创建的文件和子目录的默认值。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsCompressed`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-nameisdirectorya--cfilefindisdirectory"></a><a name="isdirectory"></a>CFileFind::IsDirectory  
 调用该成员函数以确定是否找到的文件是一个目录。  
  
```  
BOOL IsDirectory() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 是一个目录文件都标有文件属性中标识的 FILE_ATTRIBUTE_DIRECTORY [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsDirectory`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
 此小程序递归的 C:\ 驱动器上的每个目录，并输出目录的名称。  
  
 [!code-cpp[NVC_MFCFiles #&34;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]  
  
##  <a name="a-nameisdotsa--cfilefindisdots"></a><a name="isdots"></a>CFileFind::IsDots  
 调用此成员函数来测试而是循环访问文件的当前目录及其父目录标记。  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果找到的文件具有的名称，则为非"。".."，表示找到的文件是一个目录。 否则为 0。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsDots`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="a-nameishiddena--cfilefindishidden"></a><a name="ishidden"></a>CFileFind::IsHidden  
 调用该成员函数以确定是否为隐藏找到的文件。  
  
```  
BOOL IsHidden() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 中的隐藏的文件，请 FILE_ATTRIBUTE_HIDDEN 标记、 文件属性标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 隐藏的文件不包括在普通目录列表。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsHidden`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-nameisnormala--cfilefindisnormal"></a><a name="isnormal"></a>CFileFind::IsNormal  
 调用该成员函数以确定是否找到的文件是普通的文件。  
  
```  
BOOL IsNormal() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 中的文件标记为 FILE_ATTRIBUTE_NORMAL，文件属性标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 正常的文件没有设置任何其他属性。 所有其他文件属性重写此属性。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsNormal`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-nameisreadonlya--cfilefindisreadonly"></a><a name="isreadonly"></a>CFileFind::IsReadOnly  
 调用该成员函数以确定是否找到的文件是只读的。  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 用 FILE_ATTRIBUTE_READONLY 标记只读文件、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 应用程序可以读取此类文件，但不是能向其中写入数据或将其删除。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsReadOnly`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-nameissystema--cfilefindissystem"></a><a name="issystem"></a>CFileFind::IsSystem  
 调用该成员函数以确定是否找到的文件系统文件。  
  
```  
BOOL IsSystem() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 用 FILE_ATTRIBUTE_SYSTEM，标记的系统文件、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 系统文件属于，或者以独占方式，操作系统使用。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsSystem`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-nameistemporarya--cfilefindistemporary"></a><a name="istemporary"></a>CFileFind::IsTemporary  
 调用该成员函数以确定是否找到的文件是一个临时文件。  
  
```  
BOOL IsTemporary() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 临时文件都标有 FILE_ATTRIBUTE_TEMPORARY、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 临时文件用于临时存储。 仅在绝对必要时，应用程序应写入该文件。 大部分文件的数据保留在内存中而无需刷新到媒体由于很快将删除该文件。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`IsTemporary`。  
  
 请参见成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="a-namemptma--cfilefindmptm"></a><a name="m_ptm"></a>CFileFind::m_pTM  
 指向 `CAtlTransactionManager` 对象的指针。  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namematchesmaska--cfilefindmatchesmask"></a><a name="matchesmask"></a>CFileFind::MatchesMask  
 调用此成员函数来测试上找到的文件的文件属性。  
  
```  
virtual BOOL MatchesMask(DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwMask`  
 指定一个或多个中标识的文件属性[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构，找到的文件。 若要搜索的多个属性，请使用按位 OR (| | |) 运算符。 以下属性的任何组合都是可接受︰  
  
-   FILE_ATTRIBUTE_ARCHIVE 文件是一个存档文件。 应用程序使用此特性标记的备份或删除的文件。  
  
-   压缩 FILE_ATTRIBUTE_COMPRESSED 文件或目录。 对于文件，这意味着对所有文件中的数据进行压缩。 对于目录，这意味着压缩是新创建的文件和子目录的默认值。  
  
-   FILE_ATTRIBUTE_DIRECTORY 文件是一个目录。  
  
-   FILE_ATTRIBUTE_NORMAL 文件没有设置任何其他属性。 此属性是单独使用时才有效。 所有其他文件属性重写此属性。  
  
-   FILE_ATTRIBUTE_HIDDEN 文件被隐藏。 它并不是包括在普通目录列表。  
  
-   FILE_ATTRIBUTE_READONLY 文件具有只读属性。 应用程序可以读取该文件，但不能向其中写入数据或将其删除。  
  
-   该文件的一部分或由操作系统以独占方式使用 FILE_ATTRIBUTE_SYSTEM。  
  
-   FILE_ATTRIBUTE_TEMPORARY 文件用于临时存储。 仅在绝对必要时，应用程序应写入该文件。 大部分文件的数据保留在内存中而无需刷新到媒体由于很快将删除该文件。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展错误信息，请调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前，先调用`MatchesMask`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&35;](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 类](../../mfc/reference/chttpfile-class.md)

