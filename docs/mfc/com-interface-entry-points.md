---
title: COM 接口入口点
ms.date: 03/27/2019
helpviewer_keywords:
- entry points, COM interfaces
- state management, OLE/COM interfaces
- MFC COM, COM interface entry points
- OLE, interface entry points
- MFC, managing state data
- COM interfaces, entry points
ms.assetid: 9e7421dc-0731-4748-9e1b-90acbaf26d77
ms.openlocfilehash: 132dd7394119081dcaeb098c2088782ff5d40ae4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619339"
---
# <a name="com-interface-entry-points"></a>COM 接口入口点

对于 COM 接口的成员函数，使用 `METHOD_PROLOGUE` 宏在调用导出接口的方法时保持适当的全局状态。

通常，由 `CCmdTarget` 派生的对象实现的接口的成员函数已使用此宏提供 `pThis` 指针的自动初始化。 例如：

[!code-cpp[NVC_MFCConnectionPoints#5](codesnippet/cpp/com-interface-entry-points_1.cpp)]

有关其他信息，请参阅 MFC/OLE 实现上的[技术说明 38](tn038-mfc-ole-iunknown-implementation.md) `IUnknown` 。

按如下方式定义 `METHOD_PROLOGUE` 宏：

```cpp
#define METHOD_PROLOGUE(theClass, localClass) \
    theClass* pThis = \
    ((theClass*)((BYTE*)this - offsetof(theClass, m_x##localClass))); \
    AFX_MANAGE_STATE(pThis->m_pModuleState) \
```

与管理全局状态相关的宏的部分是：

`AFX_MANAGE_STATE( pThis->m_pModuleState )`

在此表达式中，假定*m_pModuleState*为包含对象的成员变量。 它由 `CCmdTarget` 基类实现，并在实例化对象时由 `COleObjectFactory` 初始化为适当的值。

## <a name="see-also"></a>另请参阅

[管理 MFC 模块的状态数据](managing-the-state-data-of-mfc-modules.md)
