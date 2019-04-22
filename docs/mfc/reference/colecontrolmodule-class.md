---
title: COleControlModule 类
ms.date: 11/04/2016
f1_keywords:
- OleControlModule
helpviewer_keywords:
- OLE control modules [MFC]
- MFC ActiveX controls [MFC], OLE control modules
- COleControlModule class [MFC]
- control modules [MFC]
ms.assetid: 0721724d-d4af-4eda-ad34-5a2b27810dd4
ms.openlocfilehash: f6d486c7bacb897d70d85414ac3d0bd0d13e447b
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58780283"
---
# <a name="colecontrolmodule-class"></a>COleControlModule 类

可以派生出 OLE 控件模块对象的基类。

## <a name="syntax"></a>语法

```
class COleControlModule : public CWinApp
```

## <a name="remarks"></a>备注

此类提供用于初始化控制模块的成员函数。 使用 Microsoft 基础类的每个 OLE 控件模块只能包含一个对象派生自`COleControlModule`。 将构造此对象时其他C++全局对象构造。 声明你派生`COleControlModule`在全局级别的对象。

有关使用的详细信息`COleControlModule`类，请参阅[CWinApp](../../mfc/reference/cwinapp-class.md)类和文章[ActiveX 控件](../../mfc/mfc-activex-controls.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

[CWinApp](../../mfc/reference/cwinapp-class.md)

`COleControlModule`

## <a name="requirements"></a>要求

**标头：** afxctl.h

## <a name="see-also"></a>请参阅

[MFC 示例 TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
