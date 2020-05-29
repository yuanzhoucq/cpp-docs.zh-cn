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
ms.openlocfilehash: ad2a9d8c5b4466a04b5a88fcce7679911bf1b81a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377016"
---
# <a name="carchiveexception-class"></a>CArchiveException 类

表示序列化异常条件

## <a name="syntax"></a>语法

```
class CArchiveException : public CException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C存档例外：C存档例外](#carchiveexception)|构造 `CArchiveException` 对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[C存档例外：：m_cause](#m_cause)|指示异常原因。|
|[C存档例外：：m_strFileName](#m_strfilename)|指定此异常条件的文件名称。|

## <a name="remarks"></a>备注

类`CArchiveException`包括指示异常原因的公共数据成员。

`CArchiveException`对象在[CArchive](../../mfc/reference/carchive-class.md)成员函数中构造和引发。 您可以在**CATCH**表达式的范围内访问这些对象。 原因代码独立于操作系统。 有关异常处理的详细信息，请参阅[异常处理 （MFC）。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a>C存档例外：C存档例外

构造`CArchiveException`对象，将*原因*的值存储在对象中。

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>参数

*原因*<br/>
指示异常原因的枚举类型变量。 有关枚举器的列表，请参阅[m_cause](#m_cause)数据成员。

*lpsz存档名称*<br/>
指向包含引起异常`CArchive`的对象名称的字符串。

### <a name="remarks"></a>备注

您可以在堆上创建`CArchiveException`一个对象，然后自己引发它，或者让全局函数[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)为您处理它。

不要直接使用此构造函数;相反，调用全局函数`AfxThrowArchiveException`。

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a>C存档例外：：m_cause

指定异常的原因。

```
int m_cause;
```

### <a name="remarks"></a>备注

此数据成员是**int**类型的公共变量。其值由`CArchiveException`枚举类型定义。 枚举器及其含义如下所示：

- `CArchiveException::none`未发生错误。

- `CArchiveException::genericException`未指定错误。

- `CArchiveException::readOnly`尝试写入打开的存档以进行加载。

- `CArchiveException::endOfFile`读取对象时到达文件结尾。

- `CArchiveException::writeOnly`尝试从打开的存档中读取以供存储。

- `CArchiveException::badIndex`无效的文件格式。

- `CArchiveException::badClass`尝试将对象读取到类型错误的对象中。

- `CArchiveException::badSchema`尝试读取具有类不同版本的对象。

    > [!NOTE]
    >  引发这些 `CArchiveException` 的枚举器不同于引发 `CFileException` 的枚举器。

    > [!NOTE]
    > `CArchiveException::generic` 已弃用。 请改用 `genericException`。 如果在应用程序中使用**泛型**并且使用 /clr 构建，则会有不容易破译的语法错误。

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a>C存档例外：：m_strFileName

指定此异常条件的文件名称。

```
CString m_strFileName;
```

## <a name="see-also"></a>另请参阅

[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CArchive 类](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[异常处理](../../mfc/reference/exception-processing.md)
