---
title: COleException 类
ms.date: 11/04/2016
f1_keywords:
- COleException
- AFXDISP/COleException
- AFXDISP/COleException::Process
- AFXDISP/COleException::m_sc
helpviewer_keywords:
- COleException [MFC], Process
- COleException [MFC], m_sc
ms.assetid: 2571e9fe-26cc-42f0-9ad9-8ad5b4311ec1
ms.openlocfilehash: 737c9e669990f4de6ae18cdc7662c131ad61516f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375015"
---
# <a name="coleexception-class"></a>COleException 类

表示与 OLE 操作相关的异常条件。

## <a name="syntax"></a>语法

```
class COleException : public CException
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle 例外：:P](#process)|将捕获的异常转换为 OLE 返回代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[COle 例外：m_sc](#m_sc)|包含指示异常原因的状态代码。|

## <a name="remarks"></a>备注

类`COleException`包括一个公共数据成员，该成员持有指示异常原因的状态代码。

通常，不应直接创建`COleException`对象，而应直接创建对象。相反，你应该调用[AfxThrowOleexception。](exception-processing.md#afxthrowoleexception)

有关异常的详细信息，请参阅[异常处理 （MFC）](../../mfc/exception-handling-in-mfc.md)和[异常：OLE 异常](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="coleexceptionm_sc"></a><a name="m_sc"></a>COle 例外：m_sc

此数据成员持有指示异常原因的 OLE 状态代码。

```
SCODE m_sc;
```

### <a name="remarks"></a>备注

此变量的值由[AfxThrowOleException](exception-processing.md#afxthrowoleexception)设置。

有关 SCODE 的详细信息，请参阅 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

## <a name="coleexceptionprocess"></a><a name="process"></a>COle 例外：:P

调用**Process**成员函数将捕获的异常转换为 OLE 状态代码。

```
static SCODE PASCAL Process(const CException* pAnyException);
```

### <a name="parameters"></a>参数

*pAnyException*<br/>
指向捕获的异常的指针。

### <a name="return-value"></a>返回值

OLE 状态代码。

### <a name="remarks"></a>备注

> [!NOTE]
> 此函数是**静态**的。

有关 SCODE 的详细信息，请参阅 Windows SDK 中的[COM 错误代码结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

## <a name="see-also"></a>另请参阅

[MFC 样品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
