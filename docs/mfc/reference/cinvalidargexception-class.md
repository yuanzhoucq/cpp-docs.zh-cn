---
title: CInvalidArgException 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInvalidArgException
- AFX/CInvalidArgException
- AFX/CInvalidArgException::CInvalidArgException
dev_langs:
- C++
helpviewer_keywords:
- CInvalidArgException [MFC], CInvalidArgException
ms.assetid: e43d7c67-1157-47f8-817a-804083e8186e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cff0727f1d194982ad76d24b0a91875448ea45c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389788"
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
