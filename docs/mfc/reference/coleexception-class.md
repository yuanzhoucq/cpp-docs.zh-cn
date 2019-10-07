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
ms.openlocfilehash: 96061f704d9df6cd788e362652b6ed22a7ffa999
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503952"
---
# <a name="coleexception-class"></a>COleException 类

表示与 OLE 操作相关的异常条件。

## <a name="syntax"></a>语法

```
class COleException : public CException
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[COleException::Process](#process)|将捕获的异常转换为 OLE 返回代码。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[COleException::m_sc](#m_sc)|包含指示异常原因的状态代码。|

## <a name="remarks"></a>备注

`COleException`类包含一个公共数据成员, 该成员保存指示异常原因的状态代码。

通常, 不应直接创建`COleException`对象; 相反, 应调用[AfxThrowOleException](exception-processing.md#afxthrowoleexception)。

有关异常的详细信息, 请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)和[异常:OLE 例外](../../mfc/exceptions-ole-exceptions.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`COleException`

## <a name="requirements"></a>要求

**标头：** afxdisp.h

##  <a name="m_sc"></a>  COleException::m_sc

此数据成员保存 OLE 状态代码, 用于指示异常的原因。

```
SCODE m_sc;
```

### <a name="remarks"></a>备注

此变量的值是由[AfxThrowOleException](exception-processing.md#afxthrowoleexception)设置的。

有关 SCODE 的详细信息, 请参阅 Windows SDK 中[COM 错误代码的结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCOleContainer#22](../../mfc/codesnippet/cpp/coleexception-class_1.cpp)]

##  <a name="process"></a>  COleException::Process

调用**进程**成员函数将捕获的异常转换为 OLE 状态代码。

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
>  此函数是**静态**的。

有关 SCODE 的详细信息, 请参阅 Windows SDK 中[COM 错误代码的结构](/windows/win32/com/structure-of-com-error-codes)。

### <a name="example"></a>示例

  请参阅 [COleDispatchDriver::CreateDispatch](../../mfc/reference/coledispatchdriver-class.md#createdispatch)的示例。

## <a name="see-also"></a>请参阅

[MFC 示例 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
