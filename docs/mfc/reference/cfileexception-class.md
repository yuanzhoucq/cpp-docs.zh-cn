---
title: CFileException 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f94d6fc19879da1dd1dcaa94ab7a177fb86d5186
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33369120"
---
# <a name="cfileexception-class"></a>CFileException 类
表示与文件相关的异常条件。  
  
## <a name="syntax"></a>语法  
  
```  
class CFileException : public CException  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CFileException::CFileException](#cfileexception)|构造 `CFileException` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CFileException::ErrnoToException](#errnotoexception)|返回导致代码对应于运行时错误号。|  
|[CFileException::GetErrorMessage](#geterrormessage)|检索描述异常的消息。|  
|[CFileException::OsErrorToException](#oserrortoexception)|返回对应于操作系统错误代码的原因代码。|  
|[CFileException::ThrowErrno](#throwerrno)|引发运行时错误号上基于文件异常。|  
|[CFileException::ThrowOsError](#throwoserror)|引发的操作系统错误号上基于文件异常。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CFileException::m_cause](#m_cause)|包含与异常的原因相对应的可移植代码。|  
|[CFileException::m_lOsError](#m_loserror)|包含相关的操作系统错误号。|  
|[CFileException::m_strFileName](#m_strfilename)|包含此异常的文件的名称。|  
  
## <a name="remarks"></a>备注  
 `CFileException`类包含保存的可移植的原因代码和特定于操作系统的错误号的公共数据成员。 类还提供了静态成员函数，为引发文件异常以及用于返回操作系统错误和 C 运行时错误的原因代码。  
  
 `CFileException` 对象了构造和中引发`CFile`成员函数和派生类的成员函数中。 你可以访问这些对象的作用域内**捕获**表达式。 对于可移植性，使用仅原因代码来获取异常的原因。 有关异常的详细信息，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CException](../../mfc/reference/cexception-class.md)  
  
 `CFileException`  
  
## <a name="requirements"></a>要求  
 **标头：** afx.h  
  
##  <a name="cfileexception"></a>  CFileException::CFileException  
 构造`CFileException`将原因代码和操作系统的代码存储在对象的对象。  
  
```  
CFileException(
    int cause = CFileException::none,  
    LONG lOsError = -1,  
    LPCTSTR lpszArchiveName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `cause`  
 一个枚举的类型变量，指示该异常的原因。 请参阅[CFileException::m_cause](#m_cause)有关可能的值的列表。  
  
 `lOsError`  
 异常，如果有一个特定于操作系统的原因。 `lOsError`参数提供的信息多于`cause`未。  
  
 `lpszArchiveName`  
 指向包含的名称的字符串`CFile`引发异常的对象。  
  
### <a name="remarks"></a>备注  
 不直接，使用此构造函数，但而是调用全局函数[AfxThrowFileException](exception-processing.md#afxthrowfileexception)。  
  
> [!NOTE]
>  变量`lOsError`仅适用于`CFile`和`CStdioFile`对象。 `CMemFile`类并不处理此错误代码。  
  
##  <a name="errnotoexception"></a>  CFileException::ErrnoToException  
 给定的运行时库错误将值转换为`CFileException`枚举错误值。  
  
```  
static int PASCAL ErrnoToException(int nErrno);
```  
  
### <a name="parameters"></a>参数  
 `nErrno`  
 整数错误代码在运行时包含文件 ERRNO 中定义。H。  
  
### <a name="return-value"></a>返回值  
 对应于给定的运行时库错误值的枚举的值。  
  
### <a name="remarks"></a>备注  
 请参阅[CFileException::m_cause](#m_cause)欲了解可能的枚举值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]  
  
##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage  
 检索描述的异常的文本。  
  
```  
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,  
    UINT nMaxError,  
    PUINT pnHelpContext = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 [in, out] `lpszError`  
 为将收到错误消息的缓冲区的指针。  
  
 [in] `nMaxError`  
 最大可以容纳指定的缓冲区的字符数。 这包括终止 null 字符。  
  
 [in, out] `pnHelpContext`  
 接收帮助上下文 id。 为无符号整数的指针 如果`NULL`，返回没有 ID。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果指定的缓冲区太小，错误消息将被截断。  
  
### <a name="example"></a>示例  
 下面的示例使用`CFileException::GetErrorMessage`。  
  
 [!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]  
  
##  <a name="m_cause"></a>  CFileException::m_cause  
 包含由 `CFileException` 枚举类型定义的值。  
  
```  
int m_cause;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员是类型 `int` 的公共变量。 枚举器及其含义如下所示：  
  
- `CFileException::none` 0： 未发生错误。  
  
- `CFileException::genericException` 1： 出现未知的错误。  
  
- `CFileException::fileNotFound` 2： 找不到文件。  
  
- `CFileException::badPath` 3： 全部或部分路径无效。  
  
- `CFileException::tooManyOpenFiles` 4： 超过了允许的打开的文件数。  
  
- `CFileException::accessDenied` 5： 无法访问该文件。  
  
- `CFileException::invalidFile` 6： 试图使用无效的文件句柄。  
  
- `CFileException::removeCurrentDir` 7： 无法删除当前工作目录。  
  
- `CFileException::directoryFull` 8： 不存在多个目录条目。  
  
- `CFileException::badSeek` 9： 时尝试设置文件指针时出错。  
  
- `CFileException::hardIO` 10： 出现了硬件错误。  
  
- `CFileException::sharingViolation` 11： 共享。未加载 EXE，或者共享的区域被锁定。  
  
- `CFileException::lockViolation` 12： 时尝试锁定已被锁定的区域。  
  
- `CFileException::diskFull` 14： 磁盘已满。  
  
- `CFileException::endOfFile` 15： 已到达文件结尾。  
  
    > [!NOTE]
    >  引发这些 `CFileException` 的枚举器不同于引发 `CArchiveException` 的枚举器。  
  
    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果在应用程序中使用 `generic` 并使用 /clr 进行生成，则生成的语法错误难以解密。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]  
  
##  <a name="m_loserror"></a>  CFileException::m_lOsError  
 包含此异常的操作系统错误代码。  
  
```  
LONG m_lOsError;  
```  
  
### <a name="remarks"></a>备注  
 请参阅你操作系统技术手册，错误代码的列表。 此数据成员是类型的公共变量**长**。  
  
##  <a name="m_strfilename"></a>  CFileException::m_strFileName  
 包含此异常条件的文件的名称。  
  
```  
CString m_strFileName;  
```  
  
##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException  
 返回一个枚举器对应于给定`lOsError`值。 如果错误代码为未知，则该函数将返回**CFileException::generic**。  
  
```  
static int PASCAL OsErrorToException(LONG lOsError);
```  
  
### <a name="parameters"></a>参数  
 `lOsError`  
 特定于操作系统的错误代码。  
  
### <a name="return-value"></a>返回值  
 对应于给定的操作系统错误值的枚举的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]  
  
##  <a name="throwerrno"></a>  CFileException::ThrowErrno  
 构造`CFileException`对象对应于给定`nErrno`值，然后引发异常。  
  
```  
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `nErrno`  
 整数错误代码在运行时包含文件 ERRNO 中定义。H。  
  
 `lpszFileName`  
 指向包含文件的名称的字符串的指针，导致异常，如果可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]  
  
##  <a name="throwoserror"></a>  CFileException::ThrowOsError  
 引发`CFileException`对应于给定`lOsError`值。 如果错误代码为未知，则该函数将引发异常编码为**CFileException::generic**。  
  
```  
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```  
  
### <a name="parameters"></a>参数  
 `lOsError`  
 特定于操作系统的错误代码。  
  
 `lpszFileName`  
 指向包含文件的名称的字符串的指针，导致异常，如果可用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [CException 类](../../mfc/reference/cexception-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [异常处理](../../mfc/reference/exception-processing.md)



