---
title: C内存异常类
ms.date: 11/04/2016
f1_keywords:
- CMemoryException
- AFX/CMemoryException
- AFX/CMemoryException::CMemoryException
helpviewer_keywords:
- CMemoryException [MFC], CMemoryException
ms.assetid: 9af0ed57-d12a-45ca-82b5-c910a60f7edf
ms.openlocfilehash: 375b4227a25ae4c18cfd263eff4c3ec13f1304e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370007"
---
# <a name="cmemoryexception-class"></a>C内存异常类

表示内存不足异常条件。

## <a name="syntax"></a>语法

```
class CMemoryException : public CSimpleException
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[内存例外：：C内存异常](#cmemoryexception)|构造 `CMemoryException` 对象。|

## <a name="remarks"></a>备注

没有必要或可能进一步的资格。 内存异常由**新**自动引发。 例如，`malloc`如果您编写自己的内存函数，则负责引发内存异常。

有关 的详细信息`CMemoryException`，请参阅文章[异常处理 （MFC）。](../../mfc/exception-handling-in-mfc.md)

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[C 例外](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CMemoryException`

## <a name="requirements"></a>要求

**标题：** afx.h

## <a name="cmemoryexceptioncmemoryexception"></a><a name="cmemoryexception"></a>内存例外：：C内存异常

构造 `CMemoryException` 对象。

```
CMemoryException();
```

### <a name="remarks"></a>备注

不要直接使用此构造函数，而是调用全局函数[AfxThrowMemoryexception](exception-processing.md#afxthrowmemoryexception)。 此全局函数可以在内存不足的情况下成功，因为它在以前分配的内存中构造异常对象。 有关异常处理的详细信息，请参阅文章[异常](../exception-handling-in-mfc.md)。

## <a name="see-also"></a>另请参阅

[CException 类](cexception-class.md)<br/>
[层次结构图表](../hierarchy-chart.md)
