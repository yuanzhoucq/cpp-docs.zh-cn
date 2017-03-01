---
title: "CREATESTRUCT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: ec72d4725cb7e5959369b24a6ff7f0e3e9da1ca7
ms.lasthandoff: 02/24/2017

---
# <a name="createstruct-structure"></a>CREATESTRUCT 结构
`CREATESTRUCT`结构定义初始化参数传递给应用程序的窗口过程。  
  
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
 `lpCreateParams`  
 指向要用于创建窗口的数据。  
  
 `hInstance`  
 标识拥有新的窗口中的模块的模块实例句柄。  
  
 `hMenu`  
 标识要使用新窗口中的菜单。 如果子窗口，将包含整数 id。  
  
 `hwndParent`  
 将拥有新的窗口的窗口。 此成员是**NULL**如果新的窗口为顶级窗口。  
  
 `cy`  
 指定新的窗口的高度。  
  
 `cx`  
 指定新的窗口的宽度。  
  
 `y`  
 指定新的窗口的左上角的 y 坐标。 如果新的窗口是一个子窗口; 坐标是相对于父窗口否则坐标是相对于屏幕的原点。  
  
 `x`  
 指定新的窗口的左上角的 x 坐标。 如果新的窗口是一个子窗口; 坐标是相对于父窗口否则坐标是相对于屏幕的原点。  
  
 `style`  
 指定新的窗口[样式](../../mfc/reference/styles-used-by-mfc.md)。  
  
 `lpszName`  
 指向以 null 结尾的字符串，它指定新窗口的名称。  
  
 `lpszClass`  
 指向以 null 结尾的字符串，它指定新窗口的窗口类名称 ( [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)结构; 有关详细信息，请参阅[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)])。  
  
 `dwExStyle`  
 指定[扩展样式](../../mfc/reference/extended-window-styles.md)新窗口。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)



