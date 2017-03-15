---
title: "CStdioFile 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStdioFile
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: f3f036b409067676fdf12db9751cac1ea8025140
ms.lasthandoff: 02/24/2017

---
# <a name="cstdiofile-class"></a>CStdioFile 类
表示由运行时函数打开的 C 运行时流文件[fopen](../../c-runtime-library/reference/fopen-wfopen.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CStdioFile : public CFile  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CStdioFile::CStdioFile](#cstdiofile)|构造`CStdioFile`从路径或文件的指针的对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CStdioFile::Open](#open)|已重载。 打开设计默认值用于`CStdioFile`构造函数 (将重写[CFile::Open](../../mfc/reference/cfile-class.md#open))。|  
|[CStdioFile::ReadString](#readstring)|读取单个文本行。|  
|[CStdioFile::Seek](#seek)|将当前的文件指针定位。|  
|[CStdioFile::WriteString](#writestring)|写入单个文本行。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CStdioFile::m_pStream](#m_pstream)|包含一个打开的文件的指针。|  
  
## <a name="remarks"></a>备注  
 流文件进行缓冲，可以在文本模式 （默认值） 或二进制模式下打开。  
  
 文本模式下提供对通过对回车-换行对特殊处理。 当你编写一个换行符 (0x0A) 字符到文本模式`CStdioFile`对象，该字节对 (0x0D，0x0A) 发送到文件。 读取时，字节对 (0x0D，0x0A) 转换成一个 0x0A 字节。  
  
 [CFile](../../mfc/reference/cfile-class.md)函数[重复](../../mfc/reference/cfile-class.md#duplicate)， [LockRange](../../mfc/reference/cfile-class.md#lockrange)，和[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)不支持`CStdioFile`。  
  
 如果在调用这些函数`CStdioFile`，您将获得[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)。  
  
 有关详细信息使用`CStdioFile`，请参阅文章[MFC 中的文件](../../mfc/files-in-mfc.md)和[文件处理](../../c-runtime-library/file-handling.md)中*运行时库参考*。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CFile](../../mfc/reference/cfile-class.md)  
  
 `CStdioFile`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="a-namecstdiofilea--cstdiofilecstdiofile"></a><a name="cstdiofile"></a>CStdioFile::CStdioFile  
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
 指定是所需的文件的路径的字符串。 路径可以是相对值还是绝对值。  
  
 `nOpenFlags`  
 指定用于创建文件、 文件共享和文件访问模式选项。 可以通过使用位或指定多个选项 ( `|`) 运算符。  
  
 一个文件访问模式选项是必需的;其他模式是可选的。 请参阅[CFile::CFile](../../mfc/reference/cfile-class.md#cfile)有关模式选项和其他标志的列表。 在 MFC 3.0 版及更高版本中，允许共享标志。  
  
 `pTM`  
 指向 CAtlTransactionManager 对象的指针。  
  
### <a name="remarks"></a>备注  
 默认构造函数不会附加到一个文件`CStdioFile`对象。 当使用此构造函数，您必须使用`CStdioFile::Open`方法打开文件并将其附加到`CStdioFile`对象。  
  
 单参数构造函数将附加到一个打开的文件流`CStdioFile`对象。 允许使用指针的值包括预定义的输入/输出文件指针`stdin`， `stdout`，或`stderr`。  
  
 两个参数构造函数创建`CStdioFile`对象并使用给定路径打开相应的文件。  
  
 如果您通过`NULL`对于任何`pOpenStream`或`lpszFileName`，构造函数引发`CInvalidArgException*`。  
  
 如果无法打开或创建该文件，在构造函数引发`CFileException*`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&37;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]  
  
##  <a name="a-namempstreama--cstdiofilempstream"></a><a name="m_pstream"></a>CStdioFile::m_pStream  
 `m_pStream`数据成员是一个指针指向一个打开的文件与由 C 运行时函数返回`fopen`。  
  
```  
FILE* m_pStream;  
```  
  
### <a name="remarks"></a>备注  
 它是**NULL**如果以前从未打开该文件，或已关闭。  
  
##  <a name="a-nameopena--cstdiofileopen"></a><a name="open"></a>CStdioFile::Open  
 已重载。 打开设计默认值用于`CStdioFile`构造函数。  
  
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
 一个字符串，是所需的文件的路径。 路径可以是相对值还是绝对值。  
  
 `nOpenFlags`  
 共享和访问模式。 指定当打开文件时要执行的操作。 您可以通过使用按位 OR (|) 运算符组合选项。 一个访问权限和一个共享选项是必需的;在 modeCreate 和 modeNoInherit 模式是可选的。  
  
 `pError`  
 指向将接收失败的操作状态的现有文件异常对象的指针。  
  
 `pTM`  
 指向 `CAtlTransactionManager` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namereadstringa--cstdiofilereadstring"></a><a name="readstring"></a>CStdioFile::ReadString  
 将文本数据读入的缓冲区最大的限制`nMax`–&1; 个字符，与关联的文件`CStdioFile`对象。  
  
```  
virtual LPTSTR ReadString(
    LPTSTR lpsz,  
    UINT nMax);  
  
virtual BOOL ReadString(CString& rString);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指定向用户提供将接收的以 null 结尾的文本字符串的缓冲区的指针。  
  
 `nMax`  
 指定的最大读取的字符数不包括终止 null 字符。  
  
 `rString`  
 对引用`CString`函数返回时，将包含字符串的对象。  
  
### <a name="return-value"></a>返回值  
 指向包含文本数据的缓冲区的指针。 **NULL**如果而无需读取任何数据; 已达到文件结尾或布尔值、 **FALSE**如果而无需读取任何数据已到达文件结尾。  
  
### <a name="remarks"></a>备注  
 读取停止了第一个换行符。 如果在这种情况下，数量少于`nMax`–&1; 字符都已读取，换行字符存储在缓冲区中。 在任一情况下将追加 null 字符 (\0)。  
  
 [CFile::Read](../../mfc/reference/cfile-class.md#read)也是可用的文本模式下输入，但它回车-换行对不会终止。  
  
> [!NOTE]
>  `CString`此函数的版本中移除`'\n'`如果存在，则`LPTSTR`版本却没有。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&38;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]  
  
##  <a name="a-nameseeka--cstdiofileseek"></a><a name="seek"></a>CStdioFile::Seek  
 在以前打开的文件指针重新定位。  
  
```  
virtual ULONGLONG Seek(
    LONGLONG lOff,  
    UINT nFrom);
```  
  
### <a name="parameters"></a>参数  
 `lOff`  
 要将指针移动的字节数。  
  
 `nFrom`  
 指针移动模式。 必须是下列值之一︰  
  
- `CFile::begin`︰ 将文件指针移`lOff`字节转发从文件的开头。  
  
- `CFile::current`︰ 将文件指针移`lOff`个字节从该文件中的当前位置。  
  
- `CFile::end`︰ 将文件指针移`lOff`个字节从文件末尾。 请注意，`lOff`必须是负才能仔细查找现有文件; 正值将查找该文件的末尾。  
  
### <a name="return-value"></a>返回值  
 如果所请求的位置是合法的`Seek`从文件的开头返回新的字节偏移量。 否则，返回值是不确定和`CFileException`抛出对象。  
  
### <a name="remarks"></a>备注  
 `Seek`函数允许随机访问的文件的内容通过移动指针指定的量，绝对或相对。 在搜索实际不读取任何数据。 如果文件的大小大于所请求的位置，文件长度将扩展到该位置，并会引发任何异常。  
  
 当打开文件时，文件指针将位于偏移量为 0，文件的开头。  
  
 这种实现`Seek`取决于运行时库 (CRT) 函数`fseek`。 有几个限制的使用情况`Seek`在文本模式下打开的流。 有关详细信息，请参阅[fseek、 _fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)。  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Seek`来移动指针 1000 个字节从开始处`cfile`文件。 请注意，`Seek`不读取数据，因此您必须随后调用[CStdioFile::ReadString](#readstring)读取数据。  
  
 [!code-cpp[NVC_MFCFiles #&39;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]  
  
##  <a name="a-namewritestringa--cstdiofilewritestring"></a><a name="writestring"></a>CStdioFile::WriteString  
 将数据从缓冲区写入与关联的文件`CStdioFile`对象。  
  
```  
virtual void WriteString(LPCTSTR lpsz);
```  
  
### <a name="parameters"></a>参数  
 `lpsz`  
 指定指向包含以 null 结尾的字符串的缓冲区的指针。  
  
### <a name="remarks"></a>备注  
 终止 null 字符 ( `\0`) 不会写入到该文件。 此方法将写入换行符`lpsz`回车/换行对形式的文件。  
  
 如果您想要写入的数据，不到文件中，使用 null 终止`CStdioFile::Write`或[CFile::Write](../../mfc/reference/cfile-class.md#write)。  
  
 此方法将引发`CInvalidArgException*`如果指定`NULL`为`lpsz`参数。  
  
 此方法将引发`CFileException*`以响应文件系统错误。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&40;](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CFile 类](../../mfc/reference/cfile-class.md)   
 [CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)   
 [CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)   
 [CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)   
 [CNotSupportedException 类](../../mfc/reference/cnotsupportedexception-class.md)

