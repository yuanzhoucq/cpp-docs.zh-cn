---
title: CREATESTRUCT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 594f71d5166261dbb1bb08422a564157bfce2721
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203656"
---
# <a name="createstruct-structure"></a>CREATESTRUCT 结构
`CREATESTRUCT`结构定义传递给应用程序的窗口过程的初始化参数。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>参数  
 *lpCreateParams*  
 指向要用于创建窗口的数据。  
  
 *hInstance*  
 标识拥有新的窗口中的模块的模块实例句柄。  
  
 *hMenu*  
 标识要由新的窗口的菜单。 如果子窗口中，将包含整数 id。  
  
 *hwndParent*  
 标识拥有新的窗口的窗口。 如果新窗口是一个顶级窗口，此成员为 NULL。  
  
 *cy*  
 指定新的窗口的高度。  
  
 *cx*  
 指定新的窗口的宽度。  
  
 *y*  
 指定新的窗口的左上角的 y 坐标。 在新窗口是子窗口; 如果坐标是相对于父窗口否则坐标是相对于屏幕源。  
  
 *x*  
 指定新的窗口的左上角的 x 坐标。 在新窗口是子窗口; 如果坐标是相对于父窗口否则坐标是相对于屏幕源。  
  
 *style*  
 指定新的窗口[样式](../../mfc/reference/styles-used-by-mfc.md)。  
  
 *lpszName*  
 指向一个以 null 结尾的字符串，指定新窗口的名称。  
  
 *lpszClass*  
 指向一个以 null 结尾的字符串，指定新窗口的 Windows 类名称 ( [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576)结构; 有关详细信息，请参阅 Windows SDK)。  
  
 *dwExStyle*  
 指定[扩展样式](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)新窗口。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


