---
title: CResourceException 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CResourceException
- AFXWIN/CResourceException
- AFXWIN/CResourceException::CResourceException
dev_langs:
- C++
helpviewer_keywords:
- CResourceException [MFC], CResourceException
ms.assetid: af6ae043-d124-4bfd-b35e-7bb0db67d289
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2e1fea7db1ef79eed2bc2678bd1e9283c71bb161
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071857"
---
# <a name="cresourceexception-class"></a>CResourceException 类

当 Windows 无法找到或分配请求的资源时生成。

## <a name="syntax"></a>语法

```
class CResourceException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CResourceException::CResourceException](#cresourceexception)|构造 `CResourceException` 对象。|

## <a name="remarks"></a>备注

没有进一步限定是需要或不能。

有关使用的详细信息`CResourceException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CResourceException`

## <a name="requirements"></a>要求

**标头:** afxwin.h

##  <a name="cresourceexception"></a>  CResourceException::CResourceException

构造 `CResourceException` 对象。

```
CResourceException();
```

### <a name="remarks"></a>备注

请勿直接，使用此构造函数而不是调用全局函数[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)。 有关异常的详细信息，请参阅文章[MFC 中的异常处理](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图](../hierarchy-chart.md)

