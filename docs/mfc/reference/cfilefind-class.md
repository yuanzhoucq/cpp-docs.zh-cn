---
title: "CFileFind 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
dev_langs: C++
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e12874dcc35c4c98b765aa773d5307d3b35dbe60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="cfilefind-class"></a>CFileFind 类
执行本地文件搜索和是为基类[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)和[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)，执行 Internet 文件搜索。  
  
## <a name="syntax"></a>语法  
  
```  
class CFileFind : public CObject  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFileFind::CFileFind](#cfilefind)|构造 `CFileFind` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileFind::Close](#close)|关闭搜索请求。|  
|[CFileFind::FindFile](#findfile)|搜索指定的文件名的目录。|  
|[CFileFind::FindNextFile](#findnextfile)|继续执行从上次调用文件搜索， [FindFile](#findfile)。|  
|[CFileFind::GetCreationTime](#getcreationtime)|获取创建文件时的时间。|  
|[CFileFind::GetFileName](#getfilename)|获取文件的名称，包括找到的文件扩展名|  
|[CFileFind::GetFilePath](#getfilepath)|获取找到的文件的整个路径。|  
|[CFileFind::GetFileTitle](#getfiletitle)|获取找到的文件的标题。 标题不包括该扩展。|  
|[CFileFind::GetFileURL](#getfileurl)|获取的 URL，包括文件路径，找到的文件。|  
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|获取上次访问文件的时间。|  
|[CFileFind::GetLastWriteTime](#getlastwritetime)|获取上次更改和保存该文件的时间。|  
|[CFileFind::GetLength](#getlength)|获取找到的文件，以字节为单位的长度。|  
|[CFileFind::GetRoot](#getroot)|获取找到的文件的根目录。|  
|[CFileFind::IsArchived](#isarchived)|确定是否存档找到的文件。|  
|[CFileFind::IsCompressed](#iscompressed)|确定是否压缩找到的文件。|  
|[CFileFind::IsDirectory](#isdirectory)|确定是否找到的文件是一个目录。|  
|[CFileFind::IsDots](#isdots)|确定是否找到的文件的名称具有名称"。".."，该值指示是实际的目录。|  
|[CFileFind::IsHidden](#ishidden)|确定是否隐藏找到的文件。|  
|[CFileFind::IsNormal](#isnormal)|确定是否找到的文件为正常 （即，没有任何其他属性）。|  
|[CFileFind::IsReadOnly](#isreadonly)|确定是否找到的文件为只读的。|  
|[CFileFind::IsSystem](#issystem)|确定找到的文件是否是系统文件。|  
|[CFileFind::IsTemporary](#istemporary)|确定是否临时找到的文件。|  
|[CFileFind::MatchesMask](#matchesmask)|指示要查找的文件的所需的文件属性。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileFind::CloseContext](#closecontext)|关闭当前的搜索句柄指定的文件。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFileFind::m_pTM](#m_ptm)|指向 `CAtlTransactionManager` 对象的指针。|  
  
## <a name="remarks"></a>备注  
 `CFileFind`包括成员函数来开始的搜索，找到文件，并返回标题、 名称或文件的路径。 对于 Internet 搜索，成员函数[GetFileURL](#getfileurl)返回文件的 URL。  
  
 `CFileFind`两个其他 MFC 类的基类设计为搜索特定服务器类型：`CGopherFileFind`专门配合 gopher 服务器和`CFtpFileFind`专门配合 FTP 服务器。 在一起，这三个类提供一种无缝机制以查找本地计算机或远程服务器上的文件，而不考虑服务器协议、 文件类型或位置，使客户端。  
  
 下面的代码将枚举在当前目录中，打印的每个文件的名称的所有文件：  
  
 [!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]  
  
 为了简化本示例，此代码使用 c + + 标准库`cout`类。 `cout`行无法替换调用`CListBox::AddString`，例如，在程序中使用图形用户界面。  
  
 有关如何使用`CFileFind`和其他 WinInet 类，请参阅文章[使用 WinInet Internet 编程](../../mfc/win32-internet-extensions-wininet.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CFileFind`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cfilefind"></a>CFileFind::CFileFind  
 此成员函数调用时`CFileFind`构造对象。  
  
```  
CFileFind();  
CFileFind(CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>参数  
 `pTM`  
 指向 CAtlTransactionManager 对象的指针  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="close"></a>CFileFind::Close  
 调用此成员函数以结束搜索、 重置上下文，并释放所有资源。  
  
```  
void Close();
```  
  
### <a name="remarks"></a>备注  
 在调用**关闭**，则不需要创建一个新`CFileFind`之前调用的实例[FindFile](#findfile)以开始新的搜索。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="closecontext"></a>CFileFind::CloseContext  
 关闭当前的搜索句柄指定的文件。  
  
```  
virtual void CloseContext();
```  
  
### <a name="remarks"></a>备注  
 关闭搜索句柄的当前值所指定的文件。 重写此函数可更改的默认行为。  
  
 必须调用[FindFile](#findfile)或[FindNextFile](#findnextfile)函数至少一次检索有效的搜索句柄。 **FindFile**和`FindNextFile`函数使用的搜索句柄来找到具有匹配具有给定名称的名称的文件。  
  
##  <a name="findfile"></a>CFileFind::FindFile  
 调用此成员函数以打开文件搜索。  
  
```  
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,  
    DWORD dwUnused = 0);
```  
  
### <a name="parameters"></a>参数  
 `pstrName`  
 指向包含要查找的文件的名称的字符串的指针。 如果你通过**NULL**为`pstrName`， **FindFile**没有通配符 (*。\*) 搜索。  
  
 *dwUnused*  
 保留以使**FindFile**多态使用派生类。 必须为 0。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 在调用**FindFile**若要开始文件搜索，调用[FindNextFile](#findnextfile)以检索后续文件。 必须调用`FindNextFile`至少一次之前调用以下属性的任何成员函数：  
  
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
  
##  <a name="findnextfile"></a>CFileFind::FindNextFile  
 调用此成员函数可继续从上次调用文件搜索[FindFile](#findfile)。  
  
```  
virtual BOOL FindNextFile();
```  
  
### <a name="return-value"></a>返回值  
 如果有多个文件; 则为非 0如果找到的文件是在目录中的最后一个，或者如果出错，则为零。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。 如果找到的文件是在目录中，最后一个文件，或者如果没有任何匹配可以找到文件，`GetLastError`函数返回 ERROR_NO_MORE_FILES。  
  
### <a name="remarks"></a>备注  
 必须调用`FindNextFile`至少一次之前调用以下属性的任何成员函数：  
  
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
  
 `FindNextFile`包装的 Win32 函数[FindNextFile](http://msdn.microsoft.com/library/windows/desktop/aa364428)。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="getcreationtime"></a>CFileFind::GetCreationTime  
 调用此成员函数可获取指定的文件的创建的时间。  
  
```  
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetCreationTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `pTimeStamp`  
 指向的指针[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含已创建了文件的时间。  
  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果不成功，则为 0。 `GetCreationTime`仅当返回 0 [FindNextFile](#findnextfile)永远不会在此调用了`CFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetCreationTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可能会返回相同的值由其他时间戳函数，如果基础的文件系统或服务器不支持保持时间属性。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 某些操作在系统上，返回的时间是在区域本地到机已在文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，有关详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="getfilename"></a>CFileFind::GetFileName  
 调用此成员函数可获取找到的文件的名称。  
  
```  
virtual CString GetFileName() const;  
```  
  
### <a name="return-value"></a>返回值  
 最近找到文件的名称。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)调用 GetFileName 以前至少一次。  
  
 `GetFileName`是的三个之一`CFileFind`成员函数将返回某种形式的文件名称。 以下列表介绍这三个和它们会有所不同：  
  
- `GetFileName`返回包括扩展名的文件名称。 例如，调用`GetFileName`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回的文件名称`myfile.txt`。  
  
- [GetFilePath](#getfilepath)返回文件的整个路径。 例如，调用`GetFilePath`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回的文件路径`c:\myhtml\myfile.txt`。  
  
- [GetFileTitle](#getfiletitle)返回不包括文件扩展名的文件名称。 例如，调用`GetFileTitle`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回文件标题`myfile`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]  
  
##  <a name="getfilepath"></a>CFileFind::GetFilePath  
 调用此成员函数可获取指定的文件的完整路径。  
  
```  
virtual CString GetFilePath() const;  
```  
  
### <a name="return-value"></a>返回值  
 指定文件的路径。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetFilePath`。  
  
 `GetFilePath`是的三个之一`CFileFind`成员函数将返回某种形式的文件名称。 以下列表介绍这三个和它们会有所不同：  
  
- [GetFileName](#getfilename)返回包括扩展名的文件名称。 例如，调用`GetFileName`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回的文件名称`myfile.txt`。  
  
- `GetFilePath`返回文件的整个路径。 例如，调用`GetFilePath`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回的文件路径`c:\myhtml\myfile.txt`。  
  
- [GetFileTitle](#getfiletitle)返回不包括文件扩展名的文件名称。 例如，调用`GetFileTitle`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回文件标题`myfile`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="getfiletitle"></a>CFileFind::GetFileTitle  
 调用此成员函数可获取找到的文件的标题。  
  
```  
virtual CString GetFileTitle() const;  
```  
  
### <a name="return-value"></a>返回值  
 文件的标题。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetFileTitle`。  
  
 `GetFileTitle`是的三个之一`CFileFind`成员函数将返回某种形式的文件名称。 以下列表介绍这三个和它们会有所不同：  
  
- [GetFileName](#getfilename)返回包括扩展名的文件名称。 例如，调用`GetFileName`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回的文件名称`myfile.txt`。  
  
- [GetFilePath](#getfilepath)返回文件的整个路径。 例如，调用`GetFilePath`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回的文件路径`c:\myhtml\myfile.txt`。  
  
- `GetFileTitle`返回不包括文件扩展名的文件名称。 例如，调用`GetFileTitle`生成有关该文件的用户消息`c:\myhtml\myfile.txt`返回文件标题`myfile`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="getfileurl"></a>CFileFind::GetFileURL  
 调用此成员函数可检索指定的 URL。  
  
```  
virtual CString GetFileURL() const;  
```  
  
### <a name="return-value"></a>返回值  
 完整的 URL。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetFileURL`。  
  
 `GetFileURL`类似于成员函数[GetFilePath](#getfilepath)，只不过它的形式返回 URL `file://path`。 例如，调用`GetFileURL`若要获取的完整 URL`myfile.txt`返回的 URL `file://c:\myhtml\myfile.txt`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="getlastaccesstime"></a>CFileFind::GetLastAccessTime  
 调用此成员函数可获取上次访问指定的文件的时间。  
  
```  
virtual BOOL GetLastAccessTime(CTime& refTime) const;  
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;  
```  
  
### <a name="parameters"></a>参数  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
 `pTimeStamp`  
 指向的指针[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含上一次访问该文件的时间。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果不成功，则为 0。 `GetLastAccessTime`仅当返回 0 [FindNextFile](#findnextfile)永远不会在此调用了`CFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLastAccessTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可能会返回相同的值由其他时间戳函数，如果基础的文件系统或服务器不支持保持时间属性。 请参阅[Win32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 某些操作在系统上，返回的时间是在区域本地到机已在文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，有关详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="getlastwritetime"></a>CFileFind::GetLastWriteTime  
 调用此成员函数可获取该文件已更改的最后一个时间。  
  
```  
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;  
virtual BOOL GetLastWriteTime(CTime& refTime) const;  
```  
  
### <a name="parameters"></a>参数  
 `pTimeStamp`  
 指向的指针[FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)结构，它包含文件上次写入到的时间。  
  
 `refTime`  
 对引用[CTime](../../atl-mfc-shared/reference/ctime-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零如果不成功，则为 0。 `GetLastWriteTime`仅当返回 0 [FindNextFile](#findnextfile)永远不会在此调用了`CFileFind`对象。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLastWriteTime`。  
  
> [!NOTE]
>  并非所有的文件系统使用相同的语义来实现此函数返回的时间戳。 此函数可能会返回相同的值由其他时间戳函数，如果基础的文件系统或服务器不支持保持时间属性。 请参阅[Win32_Find_Data](http://msdn.microsoft.com/library/windows/desktop/aa365740)有关时间格式信息的结构。 某些操作在系统上，返回的时间是在区域本地到机已在文件所在的时间。 请参阅 Win32 [FileTimeToLocalFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724277) API，有关详细信息。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="getlength"></a>CFileFind::GetLength  
 调用此成员函数可获取找到的文件，以字节为单位的长度。  
  
```  
ULONGLONG GetLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 找到文件，以字节为单位的长度。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetLength`。  
  
 `GetLength`使用 Win32 结构[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)获得和以字节为单位返回文件大小的值。  
  
> [!NOTE]
>  截至 MFC 7.0`GetLength`支持 64 位整数类型。 以前使用此较新版本的库生成的现有代码可能会导致截断警告。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]  
  
##  <a name="getroot"></a>CFileFind::GetRoot  
 调用此成员函数可获取找到的文件的根目录。  
  
```  
virtual CString GetRoot() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动的搜索的根。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`GetRoot`。  
  
 此成员函数返回的驱动器说明符和用于开始搜索的路径名称。 例如，调用[FindFile](#findfile)与`*.dat`导致`GetRoot`返回空字符串。 传递一个路径，如`c:\windows\system\*.dll`到**FindFile**结果`GetRoot`返回`c:\windows\system\`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetFileName](#getfilename)。  
  
##  <a name="isarchived"></a>CFileFind::IsArchived  
 调用此成员函数可确定是否存档找到的文件。  
  
```  
BOOL IsArchived() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 应用程序将标记一个存档文件，其中是要备份或移除了 FILE_ATTRIBUTE_ARCHIVE，文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsArchived`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="iscompressed"></a>CFileFind::IsCompressed  
 调用此成员函数可确定是否压缩找到的文件。  
  
```  
BOOL IsCompressed() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 压缩的文件都标有 FILE_ATTRIBUTE_COMPRESSED、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 对于文件，此属性可指示所有文件中的数据进行压缩。 对于目录，此属性指示压缩为新创建的文件和子目录的默认值。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsCompressed`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="isdirectory"></a>CFileFind::IsDirectory  
 调用此成员函数可确定是否找到的文件是一个目录。  
  
```  
BOOL IsDirectory() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 是一个目录文件都标有文件属性中标识的 FILE_ATTRIBUTE_DIRECTORY [WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsDirectory`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
 此小程序递归 C:\ 驱动器上的每个目录，并输出目录的名称。  
  
 [!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]  
  
##  <a name="isdots"></a>CFileFind::IsDots  
 调用此成员函数可测试循环访问文件时的当前目录及其父目录标记。  
  
```  
virtual BOOL IsDots() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果找到的文件具有名称"。".."，指示找到的文件是实际的目录。 否则为 0。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsDots`。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::IsDirectory](#isdirectory)。  
  
##  <a name="ishidden"></a>CFileFind::IsHidden  
 调用此成员函数可确定是否为隐藏找到的文件。  
  
```  
BOOL IsHidden() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 中的隐藏的文件，请使用 FILE_ATTRIBUTE_HIDDEN 标记，文件属性标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 在普通的目录列表中不包含一个隐藏的文件。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsHidden`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="isnormal"></a>CFileFind::IsNormal  
 调用此成员函数可确定找到的文件是否是正常的文件。  
  
```  
BOOL IsNormal() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 中的文件标记为 FILE_ATTRIBUTE_NORMAL，文件属性标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 普通文件具有未设置其他属性。 所有其他文件特性重写此属性。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsNormal`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="isreadonly"></a>CFileFind::IsReadOnly  
 调用此成员函数可确定是否找到的文件是只读的。  
  
```  
BOOL IsReadOnly() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 用 FILE_ATTRIBUTE_READONLY 标记只读文件，在中识别的文件属性[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 应用程序可以读取此类文件，但不是能向其写入或删除它。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsReadOnly`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="issystem"></a>CFileFind::IsSystem  
 调用此成员函数可确定找到的文件是否是系统文件。  
  
```  
BOOL IsSystem() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 用 FILE_ATTRIBUTE_SYSTEM，标记的系统文件、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 系统文件所属于的或被以独占方式，操作系统使用。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsSystem`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="istemporary"></a>CFileFind::IsTemporary  
 调用此成员函数可确定找到的文件是否是临时的文件。  
  
```  
BOOL IsTemporary() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 用 FILE_ATTRIBUTE_TEMPORARY 标记的临时文件、 文件属性中标识[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构。 临时文件用于临时存储。 仅当绝对必要，应用程序应写入到文件。 大部分文件的数据保留在内存中而不刷新到媒体因为该文件将很快被删除。  
  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`IsTemporary`。  
  
 请参阅成员函数[MatchesMask](#matchesmask)有关文件属性的完整列表。  
  
### <a name="example"></a>示例  
  请参阅示例[CFileFind::GetLength](#getlength)。  
  
##  <a name="m_ptm"></a>CFileFind::m_pTM  
 指向 `CAtlTransactionManager` 对象的指针。  
  
```  
CAtlTransactionManager* m_pTM;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="matchesmask"></a>CFileFind::MatchesMask  
 调用此成员函数可测试上找到的文件的文件属性。  
  
```  
virtual BOOL MatchesMask(DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>参数  
 `dwMask`  
 指定一个或多个标识中的文件属性[WIN32_FIND_DATA](http://msdn.microsoft.com/library/windows/desktop/aa365740)结构，找到的文件。 若要搜索多个属性，使用按位 OR (&#124;) 运算符。 以下属性的任何组合是可接受的：  
  
-   FILE_ATTRIBUTE_ARCHIVE 文件是一个存档文件。 应用程序使用此特性标记的备份或删除的文件。  
  
-   压缩 FILE_ATTRIBUTE_COMPRESSED 文件或目录。 对于文件，这意味着所有文件中的数据进行压缩。 对于一个目录，这意味着压缩是新创建的文件和子目录的默认值。  
  
-   FILE_ATTRIBUTE_DIRECTORY 文件是一个目录。  
  
-   FILE_ATTRIBUTE_NORMAL 文件没有设置任何其他属性。 此属性是单独使用时才有效。 所有其他文件特性重写此属性。  
  
-   FILE_ATTRIBUTE_HIDDEN 文件隐藏。 它是不包括在普通的目录列表。  
  
-   FILE_ATTRIBUTE_READONLY 文件具有只读属性。 应用程序可以读取该文件，但无法向其中写入或删除它。  
  
-   FILE_ATTRIBUTE_SYSTEM 该文件的一部分或操作系统被以独占方式使用。  
  
-   FILE_ATTRIBUTE_TEMPORARY 文件用于临时存储。 仅当绝对必要，应用程序应写入到文件。 大部分文件的数据保留在内存中而不刷新到媒体因为该文件将很快被删除。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。 若要获得扩展的错误信息，调用 Win32 函数[GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360)。  
  
### <a name="remarks"></a>备注  
 必须调用[FindNextFile](#findnextfile)至少一次之前调用`MatchesMask`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFtpFileFind 类](../../mfc/reference/cftpfilefind-class.md)   
 [CGopherFileFind 类](../../mfc/reference/cgopherfilefind-class.md)   
 [CInternetFile 类](../../mfc/reference/cinternetfile-class.md)   
 [CGopherFile 类](../../mfc/reference/cgopherfile-class.md)   
 [CHttpFile 类](../../mfc/reference/chttpfile-class.md)
