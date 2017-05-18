---
title: "COleControlModule 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- OleControlModule
dev_langs:
- C++
helpviewer_keywords:
- OLE control modules
- MFC ActiveX controls, OLE control modules
- COleControlModule class
- control modules
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
caps.latest.revision: 23
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
ms.sourcegitcommit: 5c6fbfc8699d7d66c40b0458972d8b6ef0dcc705
ms.openlocfilehash: 2e77c386875d25f47f0cc07eb3b7d315f1678c56
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="colecontrolmodule-class"></a>COleControlModule 类
可以派生出 OLE 控件模块对象的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>备注  
 此类提供用于初始化控制模块的成员函数。 使用 Microsoft 基础类每个 OLE 控件模块只能包含一个对象，派生自`COleControlModule`。 其他 c + + 中的全局对象在构造时，将构造此对象。 声明派生`COleControlModule`全局级别的对象。  
  
 有关详细信息使用`COleControlModule`类，请参阅[CWinApp](../../mfc/reference/cwinapp-class.md)类和文章[ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxctl.h  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 TESTHELP](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)




