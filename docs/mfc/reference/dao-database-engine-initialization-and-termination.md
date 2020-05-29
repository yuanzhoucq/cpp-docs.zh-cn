---
title: DAO 数据库引擎初始化和终止
ms.date: 09/17/2019
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 62460e8e55f70b8cb0743f1d044636d25121050d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365897"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

DAO 与 Access 数据库一起使用，并通过 Office 2013 支持。 DAO 3.6 是最终版本，它被视为过时版本。 使用 MFC DAO 对象时，必须先初始化 DAO 数据库引擎然后终止，您的应用程序或 DLL 才能退出。 `AfxDaoInit` 和 `AfxDaoTerm` 这两个函数将执行这些任务。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 数据库引擎。|
|[AfxDaoTerm](#afxdaoterm)|终止 DAO 数据库引擎。|

## <a name="afxdaoinit"></a><a name="afxdaoinit"></a>阿FXDaoinit

此功能初始化 DAO 数据库引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>备注

在大多数情况下，您不需要调用`AfxDaoInit`，因为应用程序在需要时会自动调用它。

有关相关信息，以及调用`AfxDaoInit`的示例，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="afxdaoterm"></a><a name="afxdaoterm"></a>阿FXDaoterm

此函数终止 DAO 数据库引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>备注

通常，您只需要在常规 MFC DLL 中调用此函数;否则，只需在常规 MFC DLL 中调用此函数。应用程序在需要时将自动调用`AfxDaoTerm`。

在常规 MFC DLL`AfxDaoTerm`中`ExitInstance`，在函数之前调用，但之后所有 MFC DAO 对象已销毁。

有关相关信息，请参阅[技术说明 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>要求

  **标题**afxdao.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
