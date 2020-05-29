---
title: COle调度例外类
ms.date: 11/04/2016
f1_keywords:
- COleDispatchException
- AFXDISP/COleDispatchException
- AFXDISP/COleDispatchException::m_dwHelpContext
- AFXDISP/COleDispatchException::m_strDescription
- AFXDISP/COleDispatchException::m_strHelpFile
- AFXDISP/COleDispatchException::m_strSource
- AFXDISP/COleDispatchException::m_wCode
helpviewer_keywords:
- COleDispatchException [MFC], m_dwHelpContext
- COleDispatchException [MFC], m_strDescription
- COleDispatchException [MFC], m_strHelpFile
- COleDispatchException [MFC], m_strSource
- COleDispatchException [MFC], m_wCode
ms.assetid: 0e95c8be-e21a-490c-99ec-181c6a9a26d0
ms.openlocfilehash: 4572b639b757569d8e3cfa731f99c123762f3900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375064"
---
# <a name="coledispatchexception-class"></a>COle调度例外类

处理特定于 OLE `IDispatch` 接口的异常，此接口是 OLE 自动化的重要组成部分。

## <a name="syntax"></a>语法

```
class COleDispatchException : public CException
```

## <a name="members"></a>成员

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COleDispatch例外：m_dwHelpContext](#m_dwhelpcontext)|帮助上下文查找错误。|
|[COleDispatch例外：：m_strDescription](#m_strdescription)|口头错误描述。|
|[COleDispatchException：：m_strHelpFile](#m_strhelpfile)|帮助文件与 使用`m_dwHelpContext`。|
|[COleDispatch例外：：m_strSource](#m_strsource)|生成异常的应用程序。|
|[COleDispatch例外：m_wCode](#m_wcode)|`IDispatch`-特定于错误代码。|

## <a name="remarks"></a>备注

与从`CException`基类派生的其他异常类一样，`COleDispatchException`可以使用 THROW、THROW_LAST、TRY、CATCH、AND_CATCH 和END_CATCH宏。

通常，应调用[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)来创建和引发对象`COleDispatchException`。

有关异常的详细信息，请参阅[异常处理 （MFC）](../../mfc/exception-handling-in-mfc.md)和[异常：OLE 异常](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`COleDispatchException`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="coledispatchexceptionm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>COleDispatch例外：m_dwHelpContext

在应用程序的帮助 （中标识帮助上下文。HLP）文件。

```
DWORD m_dwHelpContext;
```

### <a name="remarks"></a>备注

此成员由函数[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)设置，当引发异常时。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

## <a name="coledispatchexceptionm_strdescription"></a><a name="m_strdescription"></a>COleDispatch例外：：m_strDescription

包含口头错误描述，如"磁盘已满"。

```
CString m_strDescription;
```

### <a name="remarks"></a>备注

此成员由函数[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)设置，当引发异常时。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

## <a name="coledispatchexceptionm_strhelpfile"></a><a name="m_strhelpfile"></a>COleDispatchException：：m_strHelpFile

框架用应用程序的帮助文件的名称填充此字符串。

```
CString m_strHelpFile;
```

## <a name="coledispatchexceptionm_strsource"></a><a name="m_strsource"></a>COleDispatch例外：：m_strSource

框架用生成异常的应用程序的名称填充此字符串。

```
CString m_strSource;
```

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

## <a name="coledispatchexceptionm_wcode"></a><a name="m_wcode"></a>COleDispatch例外：m_wCode

包含特定于应用程序的错误代码。

```
WORD m_wCode;
```

### <a name="remarks"></a>备注

此成员由函数[AfxThrowOleDispatchException](exception-processing.md#afxthrowoledispatchexception)设置，当引发异常时。

## <a name="see-also"></a>另请参阅

[MFC 样品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[COleDispatchDriver 类](../../mfc/reference/coledispatchdriver-class.md)<br/>
[COleException 类](../../mfc/reference/coleexception-class.md)
