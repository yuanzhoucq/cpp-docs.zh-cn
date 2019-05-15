---
title: DAO 数据库引擎初始化和终止
ms.date: 11/04/2016
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 1b8186627f00105cf782586060b41ae0fb627d76
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611934"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

使用 MFC DAO 对象时，必须先初始化 DAO 数据库引擎然后终止，您的应用程序或 DLL 才能退出。 `AfxDaoInit` 和 `AfxDaoTerm` 这两个函数将执行这些任务。

### <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

|||
|-|-|
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 数据库引擎。|
|[AfxDaoTerm](#afxdaoterm)|终止 DAO 数据库引擎。|

##  <a name="afxdaoinit"></a>  AfxDaoInit

此函数将初始化 DAO 数据库引擎。

```

void AfxDaoInit();

throw(CDaoException*);
```

### <a name="remarks"></a>备注

在大多数情况下，您无需调用`AfxDaoInit`因为应用程序会自动调用它时需要它。

有关相关信息，并调用示例`AfxDaoInit`，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>要求

  **标头**afxdao.h

##  <a name="afxdaoterm"></a>  AfxDaoTerm

此函数将终止 DAO 数据库引擎。

```

void AfxDaoTerm();
```

### <a name="remarks"></a>备注

通常情况下，只需在 MFC DLL; 正则表达式中调用此函数应用程序将自动调用`AfxDaoTerm`需要时。

在规则 MFC Dll，调用`AfxDaoTerm`之前`ExitInstance`函数，但销毁所有 MFC DAO 对象之后。

有关相关信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。

### <a name="requirements"></a>要求

  **标头**afxdao.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
