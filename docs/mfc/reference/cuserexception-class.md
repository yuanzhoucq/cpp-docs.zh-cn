---
title: CUserException 类
ms.date: 11/04/2016
f1_keywords:
- CUserException
helpviewer_keywords:
- operations [MFC], stopping
- exceptions [MFC], throwing
- CUserException class [MFC]
- errors [MFC], trapping
- operations [MFC]
- throwing exceptions [MFC], stopping user operations
ms.assetid: 2156ba6d-2cce-415a-9000-6f02c26fcd7d
ms.openlocfilehash: 72d8537616792859a2b00a1a5cd880ce5eb452bf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323432"
---
# <a name="cuserexception-class"></a>CUserException 类

引发后将终止最终用户操作。

## <a name="syntax"></a>语法

```
class CUserException : public CSimpleException
```

## <a name="remarks"></a>备注

使用`CUserException`何时应使用 throw/catch 异常机制使用的特定于应用程序的异常。 "用户"中的类名可解释为"我的用户就算我需要处理异常。"

一个`CUserException`调用全局函数后，就会引发`AfxMessageBox`通知的用户的操作已失败。 在编写异常处理程序时，特别是因为用户通常已通知失败的处理异常。 在某些情况下，框架会引发此异常。 若要引发`CUserException`自己，提醒用户，然后调用全局函数`AfxThrowUserException`。

在下面的示例中，包含可能会失败的操作的函数向用户发出警报，并引发`CUserException`。 调用函数会捕获此异常，并专门对其进行处理：

[!code-cpp[NVC_MFCExceptions#24](../../mfc/codesnippet/cpp/cuserexception-class_1.cpp)]

有关使用的详细信息`CUserException`，请参阅文章[异常处理 (MFC)](../../mfc/exception-handling-in-mfc.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

[CSimpleException](../../mfc/reference/csimpleexception-class.md)

`CUserException`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CException 类](../../mfc/reference/cexception-class.md)
