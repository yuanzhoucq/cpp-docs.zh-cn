---
title: CArchiveException 类
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: 731735bccf9225e67d82b1fe90336c92a630b368
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855254"
---
# <a name="carchiveexception-class"></a>CArchiveException 类

表示序列化异常条件

## <a name="syntax"></a>语法

```
class CArchiveException : public CException
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|构造 `CArchiveException` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CArchiveException：： m_cause](#m_cause)|指示异常的原因。|
|[CArchiveException：： m_strFileName](#m_strfilename)|为此异常条件指定文件的名称。|

## <a name="remarks"></a>备注

`CArchiveException` 类包括指示异常原因的公共数据成员。

`CArchiveException` 对象在[CArchive](../../mfc/reference/carchive-class.md)成员函数内构造和引发。 您可以在**CATCH**表达式的作用域内访问这些对象。 原因代码与操作系统无关。 有关异常处理的详细信息，请参阅[异常处理（MFC）](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="carchiveexception"></a>CArchiveException::CArchiveException

构造一个 `CArchiveException` 对象，并在对象中存储*原因*的值。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>参数

*cause*<br/>
指示异常原因的枚举类型变量。 有关枚举器的列表，请参阅[m_cause](#m_cause)数据成员。

*lpszArchiveName*<br/>
指向一个字符串，该字符串包含导致异常的 `CArchive` 对象的名称。

### <a name="remarks"></a>备注

你可以在堆上创建一个 `CArchiveException` 对象，并自行引发该对象，或让全局函数[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)处理它。

不要直接使用此构造函数;相反，请 `AfxThrowArchiveException`调用 global 函数。

##  <a name="m_cause"></a>CArchiveException：： m_cause

指定异常的原因。

```
int m_cause;
```

### <a name="remarks"></a>备注

此数据成员是**int**类型的公共变量。它的值由 `CArchiveException` 枚举类型来定义。 枚举器及其含义如下所示：

- `CArchiveException::none` 未发生错误。

- `CArchiveException::genericException` 未指定的错误。

- `CArchiveException::readOnly` 尝试写入已打开用于加载的存档。

- 读取对象时，`CArchiveException::endOfFile` 已到达文件结尾。

- `CArchiveException::writeOnly` 尝试从打开的存储进行读取。

- `CArchiveException::badIndex` 文件格式无效。

- `CArchiveException::badClass` 尝试将对象读入错误类型的对象。

- `CArchiveException::badSchema` 尝试使用不同版本的类读取对象。

    > [!NOTE]
    >  引发这些 `CArchiveException` 的枚举器不同于引发 `CFileException` 的枚举器。

    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果在应用程序中使用**泛型**，并使用/clr 生成，则会出现语法错误，不容易解密。

##  <a name="m_strfilename"></a>CArchiveException：： m_strFileName

为此异常条件指定文件的名称。

```
CString m_strFileName;
```

## <a name="see-also"></a>另请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CArchive 类](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[异常处理](../../mfc/reference/exception-processing.md)
