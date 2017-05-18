---
title: "DAO 数据库引擎初始化和终止 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.macros.data
dev_langs:
- C++
helpviewer_keywords:
- DAO (Data Access Objects), termination
- DAO (Data Access Objects), initialization
ms.assetid: a7edf31c-e7c2-4f3e-aada-63c3e48781da
caps.latest.revision: 13
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: b6119279234558998fad1f220239a29618c69cc5
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止
使用 MFC DAO 对象时，必须先初始化 DAO 数据库引擎然后终止，您的应用程序或 DLL 才能退出。 `AfxDaoInit` 和 `AfxDaoTerm` 这两个函数将执行这些任务。  
  
### <a name="dao-database-engine-initialization-and-termination"></a>DAO 数据库引擎初始化和终止  
  
|||  
|-|-|  
|[AfxDaoInit](#afxdaoinit)|初始化 DAO 数据库引擎。|  
|[AfxDaoTerm](#afxdaoterm)|终止 DAO 数据库引擎。|  
  
##  <a name="afxdaoinit"></a>AfxDaoInit  
 此函数将初始化 DAO 数据库引擎。  
  
```  
 
void AfxDaoInit();

throw(CDaoException*);  
```  
  
### <a name="remarks"></a>备注  
 在大多数情况下，您不需要调用`AfxDaoInit`因为应用程序将自动调用它时需要它。  
  
 有关相关信息，并以举例说明如何调用`AfxDaoInit`，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  
  
### <a name="requirements"></a>要求  
  **标头**afxdao.h  
  
##  <a name="afxdaoterm"></a>AfxDaoTerm  
 此函数将终止 DAO 数据库引擎。  
  
```  
 
void AfxDaoTerm();  
```  
  
### <a name="remarks"></a>备注  
 通常情况下，只需调用此函数的规则 DLL; 中应用程序将自动调用`AfxDaoTerm`需要时。  
  
 在规则 Dll 中，调用`AfxDaoTerm`之前`ExitInstance`函数，但在所有 MFC DAO 对象被都销毁后。  
  
 有关相关信息，请参阅[技术注意 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)。  

### <a name="requirements"></a>要求  
  **标头**afxdao.h  

## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

