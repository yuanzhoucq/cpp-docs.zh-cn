---
title: DAO 数据库引擎初始化和终止
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.data
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
ms.openlocfilehash: 8ad0c1df2f5b6a7b1b48d2db119b04e4b3234f10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297628"
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止

使用 MFC DAO 对象时，必须先初始化 DAO 数据库引擎然后终止，您的应用程序或 DLL 才能退出。 
  `AfxDaoInit` 和 `AfxDaoTerm` 这两个函数将执行这些任务。

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
