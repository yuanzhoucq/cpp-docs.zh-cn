---
title: COleControlModule 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- OleControlModule
dev_langs:
- C++
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 597639145385f4aabcba0e83fef855f7a0779f9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="colecontrolmodule-class"></a>COleControlModule 类
可以派生出 OLE 控件模块对象的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleControlModule : public CWinApp  
```  
  
## <a name="remarks"></a>备注  
 此类提供用于初始化控制模块的成员函数。 每个 OLE 控件模块，使用 Microsoft 基础类只能包含一个对象派生自`COleControlModule`。 其他 c + + 全局对象在构造时，将构造此对象。 声明你派生`COleControlModule`在全局级别的对象。  
  
 有关详细信息使用`COleControlModule`类，请参阅[CWinApp](../../mfc/reference/cwinapp-class.md)类和文章[ActiveX 控件](../../mfc/mfc-activex-controls.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 [CWinApp](../../mfc/reference/cwinapp-class.md)  
  
 `COleControlModule`  
  
## <a name="requirements"></a>要求  
 **标头：** afxctl.h  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 TESTHELP](../../visual-cpp-samples.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



