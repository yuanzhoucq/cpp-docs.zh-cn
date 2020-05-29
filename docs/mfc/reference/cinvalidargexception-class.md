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
ms.openlocfilehash: b28b6e84043b85a8117694a67ff5fff13e7c786b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372367"
---
# <a name="cinvalidargexception-class"></a>CInvalidArgException 类

此类表示一个无效自变量异常条件。

## <a name="syntax"></a>语法

```
class CInvalidArgException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CInvalidArg例外：CInvalidArg例外](#cinvalidargexception)|构造函数。|

## <a name="remarks"></a>备注

对象`CInvalidArgException`表示无效的参数异常条件。

有关异常处理的详细信息，请参阅["例外类](../../mfc/reference/cexception-class.md)"主题和[异常处理 （MFC）。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CInvalidArgException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cinvalidargexceptioncinvalidargexception"></a><a name="cinvalidargexception"></a>CInvalidArg例外：CInvalidArg例外

构造函数。

```
CInvalidArgException();
```

### <a name="remarks"></a>备注

不要直接使用此构造函数;调用全局函数**AfxThrow 无效点异常**。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CSimpleException 类](../../mfc/reference/csimpleexception-class.md)
