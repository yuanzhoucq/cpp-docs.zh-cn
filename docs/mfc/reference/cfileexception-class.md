---
title: "CFileException 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
dev_langs:
- C++
helpviewer_keywords:
- CFile class, exceptions of
- exceptions, file type
- CFileException class
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d9064ae66f0dcd0e9f0dce0eedd8e38353f9da06
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cfileexception-class"></a>CFileException 类
表示与文件相关的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CFileException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CFileException::CFileException](#cfileexception)|构造 `CFileException` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CFileException::ErrnoToException](#errnotoexception)|返回导致与运行时错误号相对应的代码。|  
|[CFileException::GetErrorMessage](#geterrormessage)|检索描述异常的消息。|  
|[CFileException::OsErrorToException](#oserrortoexception)|返回对应于操作系统错误代码的原因代码。|  
|[CFileException::ThrowErrno](#throwerrno)|将引发运行时错误号上基于文件例外。|  
|[CFileException::ThrowOsError](#throwoserror)|将引发文件例外根据操作系统错误号。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFileException::m_cause](#m_cause)|包含与异常原因相对应的可移植代码。|  
|[CFileException::m_lOsError](#m_loserror)|包含相关的操作系统错误号。|  
|[CFileException::m_strFileName](#m_strfilename)|包含此异常的文件的名称。|  
  
## <a name="remarks"></a>备注  
 `CFileException`类包含保存的可移植的原因代码和特定于操作系统的错误号的公共数据成员。 该类还提供静态成员函数的引发文件异常以及用于返回操作系统错误和 C 运行时错误的原因代码。  
  
 `CFileException`对象是构造类型，引发`CFile`成员函数和派生类的成员函数中。 您可以访问这些对象的作用域内**捕获**表达式。 出于可移植性，使用仅原因代码获取异常的原因。 关于异常的详细信息，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cfileexception"></a>CFileException::CFileException  
 构造`CFileException`对象中存储的原因代码和操作系统代码的对象。  
  
```  
CFileException(
    int cause = CFileException::none,  
    LONG lOsError = -1,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cause`  
 一个枚举的类型变量，指示该异常的原因。 请参阅[CFileException::m_cause](#m_cause)有关的可能值列表。  
  
 `lOsError`  
 该异常，如果有特定于操作系统的原因。 `lOsError`参数提供的信息多于`cause`未。  
  
 `lpszArchiveName`  
 指向包含名称的字符串`CFile`导致此异常的对象。  
  
### <a name="remarks"></a>备注  
 不直接使用此构造函数，但而是调用全局函数[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。  
  
> [!NOTE]
>  该变量`lOsError`仅适用于`CFile`和`CStdioFile`对象。 `CMemFile`类不处理此错误代码。  
  
##  <a name="errnotoexception"></a>CFileException::ErrnoToException  
 将给定的运行时库的错误值到转换`CFileException`枚举错误值。  
  
```  
static int PASCAL ErrnoToException(int nErrno);
```  
  
### <a name="parameters"></a>参数  
 `nErrno`  
 在运行时包含文件 ERRNO 中定义的整数错误代码。H。  
  
### <a name="return-value"></a>返回值  
 为给定的运行时库的错误值相对应的枚举的值。  
  
### <a name="remarks"></a>备注  
 请参阅[CFileException::m_cause](#m_cause)欲了解可能的枚举值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&26;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]  
  
##  <a name="geterrormessage"></a>CFileException::GetErrorMessage  
 检索描述一种异常的文本。  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,  
    UINT nMaxError,  
    PUINT pnHelpContext = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 [in, out] `lpszError`  
 指向接收一条错误消息的缓冲区的指针。  
  
 [in] `nMaxError`  
 最大可以容纳指定的缓冲区的字符数。 这包括终止 null 字符。  
  
 [in, out] `pnHelpContext`  
 为接收帮助上下文 id。 无符号整数的指针 如果`NULL`，则返回没有 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果指定的缓冲区太小，错误消息将被截断。  
  
### <a name="example"></a>示例  
 下面的示例使用`CFileException::GetErrorMessage`。  
  
 [!code-cpp[NVC_MFCExceptions #&22;](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]  
  
##  <a name="m_cause"></a>CFileException::m_cause  
 包含由 `CFileException` 枚举类型定义的值。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员是类型 `int` 的公共变量。 枚举器及其含义如下所示：  
  
- `CFileException::none`0︰ 未发生错误。  
  
- `CFileException::genericException`1︰ 出现未知的错误。  
  
- `CFileException::fileNotFound`2︰ 找不到文件。  
  
- `CFileException::badPath`3︰ 全部或部分路径无效。  
  
- `CFileException::tooManyOpenFiles`4︰ 超过了允许的打开的文件数。  
  
- `CFileException::accessDenied`5︰ 无法访问该文件。  
  
- `CFileException::invalidFile`6︰ 试图使用无效的文件句柄。  
  
- `CFileException::removeCurrentDir`7︰ 不能删除当前工作目录。  
  
- `CFileException::directoryFull`8︰ 没有更多的目录条目。  
  
- `CFileException::badSeek`9︰ 时尝试设置文件指针时出错。  
  
- `CFileException::hardIO`10︰ 硬件错误。  
  
- `CFileException::sharingViolation`11︰ 共享。未加载 EXE，或共享的区域已被锁定。  
  
- `CFileException::lockViolation`12︰ 尝试锁定已经锁定的区域。  
  
- `CFileException::diskFull`14︰ 磁盘已满。  
  
- `CFileException::endOfFile`15︰ 已到达文件末尾。  
  
    > [!NOTE]
    >  引发这些 `CFileException` 的枚举器不同于引发 `CArchiveException` 的枚举器。  
  
    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果在应用程序中使用 `generic` 并使用 /clr 进行生成，则生成的语法错误难以解密。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&30;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]  
  
##  <a name="m_loserror"></a>CFileException::m_lOsError  
 包含此异常的操作系统错误代码。  
  
```  
LONG m_lOsError;  
```  
  
### <a name="remarks"></a>备注  
 请参阅您操作系统技术手册来查找错误代码的列表。 此数据成员是类型的公共变量**长**。  
  
##  <a name="m_strfilename"></a>CFileException::m_strFileName  
 包含此异常条件的文件的名称。  
  
```  
CString m_strFileName;  
```  
  
##  <a name="oserrortoexception"></a>CFileException::OsErrorToException  
 返回一个枚举器对应于给定`lOsError`值。 如果错误代码为未知的则该函数返回**CFileException::generic**。  
  
```  
static int PASCAL OsErrorToException(LONG lOsError);
```  
  
### <a name="parameters"></a>参数  
 `lOsError`  
 特定于操作系统的错误代码。  
  
### <a name="return-value"></a>返回值  
 对应于给定的操作系统错误值的枚举的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&27;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]  
  
##  <a name="throwerrno"></a>CFileException::ThrowErrno  
 构造`CFileException`对象对应于给定`nErrno`值，然后引发异常。  
  
```  
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nErrno`  
 在运行时包含文件 ERRNO 中定义的整数错误代码。H。  
  
 `lpszFileName`  
 指向包含该文件的名称的字符串的指针，该异常，如果导致可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&28;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]  
  
##  <a name="throwoserror"></a>CFileException::ThrowOsError  
 引发`CFileException`对应于给定`lOsError`值。 如果错误代码为未知，则该函数将引发异常的编码与**CFileException::generic**。  
  
```  
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lOsError`  
 特定于操作系统的错误代码。  
  
 `lpszFileName`  
 指向包含该文件的名称的字符串的指针，该异常，如果导致可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles #&29;](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]  
  
## <a name="see-also"></a>另请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [异常处理](../../mfc/reference/exception-processing.md)




