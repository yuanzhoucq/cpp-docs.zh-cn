---
title: DAO 数据库引擎初始化和终止 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f28c0c166bcbf13181161d6afce484fe4a45b80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止
使用 MFC DAO 对象时，必须先初始化 DAO 数据库引擎然后终止，您的应用程序或 DLL 才能退出。 `AfxDaoInit` 和 `AfxDaoTerm` 这两个函数将执行这些任务。  
  
### <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 数据库引擎。|  
|[AfxDaoTerm](#afxdaoterm)|终止 DAO 数据库引擎。|  
  
##  <a name="afxdaoinit"></a>  AfxDaoInit  
 此函数初始化 DAO 数据库引擎。  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，你无需调用`AfxDaoInit`由于应用程序自动调用它时需要它。  
  
 有关相关信息，并调用示例`AfxDaoInit`，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="afxdaoterm"></a>  AfxDaoTerm  
 此函数将终止 DAO 数据库引擎。  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>备注  
 通常情况下，只需调用此函数在正则表达式 MFC DLL;应用程序将自动调用`AfxDaoTerm`需要时。  
  
 在 MFC 的规则 Dll，调用`AfxDaoTerm`之前`ExitInstance`函数，但在所有 MFC DAO 对象已被都销毁。  
  
 有关相关信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  

### <a name="requirements"></a>要求  
  **标头**afxdao.h  

## <a name="see-also"></a>请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
