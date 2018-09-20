---
title: CMemoryException 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
dev_langs:
- C++
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 028c74bdc0c937fe59b621b81fb6abb8def63707
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385100"
---
# <a name="cmemoryexception-class"></a>CMemoryException 类

表示内存不足异常条件。

## <a name="syntax"></a>语法

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMemoryException::CMemoryException](#cmemoryexception)|构造 `CMemoryException` 对象。|

## <a name="remarks"></a>备注

没有进一步限定是需要或不能。 会自动引发内存异常**新**。 如果您编写您自己的内存的函数，使用`malloc`，对于示例中，则你负责引发内存异常。

有关详细信息`CMemoryException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>要求

**标头：** afx.h

##  <a name="cmemoryexception"></a>  CMemoryException::CMemoryException

构造 `CMemoryException` 对象。

```
CMemoryException();
```

### <a name="remarks"></a>备注

请勿直接，使用此构造函数而不是调用全局函数[AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)。 此全局函数可以在内存不足情况下成功，因为它构造以前分配的内存中的异常对象。 有关异常处理的详细信息，请参阅文章[异常](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图](../hierarchy-chart.md)



