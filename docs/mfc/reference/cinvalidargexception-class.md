---
title: CInvalidArgException 类
ms.date: 11/04/2016
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
ms.openlocfilehash: d2df9b482fe95ad0a13a85a51037a4cbbc28d057
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392616"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException 类

此类表示一个无效自变量异常条件。

## <a name="syntax"></a>语法

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CInvalidArgException::CInvalidArgException](#cinvalidargexception)|构造函数。|

## <a name="remarks"></a>备注

一个`CInvalidArgException`对象表示的参数无效异常条件。

异常处理的详细信息，请参阅[CException 类](../../mfc/reference/cexception-class.md)主题和[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cinvalidargexception"></a>  CInvalidArgException::CInvalidArgException

构造函数。

```
CInvalidArgException();
```

### <a name="remarks"></a>备注

直接调用不使用此构造函数调用全局函数**AfxThrowInvalidArgException**。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException 类](../../mfc/reference/csimpleexception-class.md)
