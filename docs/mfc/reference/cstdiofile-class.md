---
title: "CStdioFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
dev_langs:
- C++
helpviewer_keywords:
- CStdioFile class
- I/O [MFC], stream
- stream I/O
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 6b334c2973a2567a8a9bd16a80bd4c3628ced6d2
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="cstdiofile-class"></a>CStdioFile 类
表示 C 运行时流文件，并由运行时函数打开[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|构造`CStdioFile`从路径或文件指针的对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|已重载。 打开专用于默认值`CStdioFile`构造函数 (重写[CFile::Open](../../mfc/reference/cfile-class.md#open))。|  
|[CStdioFile::ReadString](#readstring)|读取单个文本行。|  
|[CStdioFile::Seek](#seek)|当前的文件指针定位。|  
|[CStdioFile::WriteString](#writestring)|写入单个文本行。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|包含指向打开的文件的指针。|  
  
## <a name="remarks"></a>备注  
 流文件进行缓冲，可以在文本模式 （默认） 还是二进制模式中打开。  
  
 文本模式下提供对回车换行符对特殊处理。 当你编写的换行符字符到文本模式 (0x0A)`CStdioFile`对象、 字节对 (0x0D，0x0A) 发送到文件。 读取时，字节对 (0x0D，0x0A) 转换为单 0x0A 字节。  
  
 [CFile](../../mfc/reference/cfile-class.md)函数[重复](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)不支持`CStdioFile`。  
  
 如果你对调用这些函数`CStdioFile`，你将获得[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 有关详细信息使用`CStdioFile`，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)和[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cstdiofile"></a>CStdioFile::CStdioFile  
 构造并初始化一个 `CStdioFile` 对象。  
  
```  
CStdioFile();  
CStdioFile(CAtlTransactionManager* pTM);  
  CStdioFile(FILE* pOpenStream);

 
CStdioFile(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags);

 
CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```  
  
### <a name="parameters"></a>参数  
 `pOpenStream`  
 指定对 C 运行时函数的调用返回的文件指针[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
 `lpszFileName`  
 指定是所需的文件的路径的字符串。 路径可以是相对或绝对。  
  
 `nOpenFlags`  
 指定文件创建、 文件共享和文件访问模式的选项。 你可以使用的按位或指定多个选项 ( `|`) 运算符。  
  
 一个文件访问模式选项是必需的;其他模式是可选的。 请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)有关模式选项和其他标志的列表。 在 MFC 3.0 版及更高版本，允许共享标志。  
  
 `pTM`  
 指向 CAtlTransactionManager 对象的指针。  
  
### <a name="remarks"></a>备注  
 默认构造函数不会附加的文件，以便`CStdioFile`对象。 在使用此构造函数，您必须使用`CStdioFile::Open`方法打开文件并将其附加到`CStdioFile`对象。  
  
 单参数构造函数将附加到的打开的文件流`CStdioFile`对象。 允许指针的值包括预定义的输入/输出文件指针`stdin`， `stdout`，或`stderr`。  
  
 两个参数构造函数创建`CStdioFile`对象，并将相应的文件打开与给定的路径。  
  
 如果你通过`NULL`为`pOpenStream`或`lpszFileName`，在构造函数引发`CInvalidArgException*`。  
  
 如果无法打开或创建文件，在构造函数引发`CFileException*`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles # 37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="m_pstream"></a>CStdioFile::m_pStream  
 `m_pStream`数据成员是由 C 运行时函数返回指向打开的文件的指针`fopen`。  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>备注  
 它是**NULL**如果文件从未打开或已关闭。  
  
##  <a name="open"></a>CStdioFile::Open  
 已重载。 打开专用于默认值`CStdioFile`构造函数。  
  
```  
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CFileException* pError = NULL);

 
virtual BOOL Open(
    LPCTSTR lpszFileName,  
    UINT nOpenFlags,  
    CAtlTransactionManager* pTM,  
    CFileException* pError = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lpszFileName`  
 一个字符串，是所需的文件的路径。 路径可以是相对或绝对。  
  
 `nOpenFlags`  
 共享和访问模式。 指定当打开文件时要执行的操作。 你可以通过使用按位 OR (|) 运算符组合选项。 一个访问权限和一个共享选项是必需的;modeCreate 和 modeNoInherit 模式是可选的。  
  
 `pError`  
 指向将接收失败的操作的状态的现有文件异常对象的指针。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="readstring"></a>CStdioFile::ReadString  
 将文本数据读入的缓冲区，最多为`nMax`-1 个字符，与关联的文件从`CStdioFile`对象。  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指定指向用户提供将接收的以 null 结尾的文本字符串的缓冲区的指针。  
  
 `nMax`  
 指定的最大读取的字符数不包括终止 null 字符。  
  
 `rString`  
 对引用`CString`在函数返回时，将包含字符串的对象。  
  
### <a name="return-value"></a>返回值  
 指向包含文本数据的缓冲区的指针。 **NULL**如果文件尾已达到而无需读取任何数据; 或如果布尔值、 **FALSE**如果而无需读取任何数据已到达最终的文件。  
  
### <a name="remarks"></a>备注  
 读取已停止的第一个换行符。 如果，在这种情况下，比较少`nMax`-1 字符都已读取，换行字符存储在缓冲区中。 在任一情况下将追加 null 字符 (\0)。  
  
 [CFile::Read](../../mfc/reference/cfile-class.md#read)有也可用的文本模式下输入，但它不会终止回车换行符对上。  
  
> [!NOTE]
>  `CString`此函数的版本中移除`'\n'`如果存在;`LPTSTR`版本却没有。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles # 38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="seek"></a>CStdioFile::Seek  
 在先前已打开的文件指针重新定位。  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>参数  
 `lOff`  
 要将指针移动到的字节数。  
  
 `nFrom`  
 指针移动模式。 必须是以下值之一︰  
  
- `CFile::begin`︰ 移动文件指针`lOff`转发中文件的开头的字节。  
  
- `CFile::current`︰ 移动文件指针`lOff`个字节从文件中的当前位置。  
  
- `CFile::end`︰ 移动文件指针`lOff`从文件末尾的字节。 请注意，`lOff`必须负要查找到现有文件; 正值将查找该文件的末尾。  
  
### <a name="return-value"></a>返回值  
 如果所请求的位置是合法的`Seek`返回文件的开头的新的字节偏移量。 否则，返回值是不确定和`CFileException`引发对象。  
  
### <a name="remarks"></a>备注  
 `Seek`函数允许随机访问文件的内容通过移动指针指定的量，绝对或相对。 在查找期间实际不读取任何数据。 如果所请求的位置大于文件的大小，文件长度将扩展到的位置，并且会引发任何异常。  
  
 当打开文件时，文件指针将位于偏移量为 0，文件的开头。  
  
 此实现的`Seek`基于运行时库 (CRT) 函数`fseek`。 有几个限制的使用情况`Seek`上在文本模式下打开的流。 有关详细信息，请参阅[fseek、 _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Seek`来移动指针 1000 个字节从开始处`cfile`文件。 请注意，`Seek`不会读取数据，因此您必须随后调用[CStdioFile::ReadString](#readstring)读取数据。  
  
 [!code-cpp[NVC_MFCFiles # 39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="writestring"></a>CStdioFile::WriteString  
 将数据从缓冲区写入与关联的文件`CStdioFile`对象。  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指定指向包含以 null 结尾的字符串的缓冲区的指针。  
  
### <a name="remarks"></a>备注  
 终止 null 字符 ( `\0`) 不会写入该文件。 此方法中写入换行符`lpsz`为回车/换行对的文件。  
  
 如果你想要写入的数据，不到文件中，使用以 null 结尾`CStdioFile::Write`或[CFile::Write](../../mfc/reference/cfile-class.md#write)。  
  
 此方法将引发`CInvalidArgException*`如果指定`NULL`为`lpsz`参数。  
  
 此方法将引发`CFileException*`以响应文件系统错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles # 40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)

