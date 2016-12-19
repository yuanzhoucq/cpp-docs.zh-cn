---
title: "CREATESTRUCT 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATESTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CREATESTRUCT 结构"
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: 14
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CREATESTRUCT 结构
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CREATESTRUCT` 结构定义初始化参数传递给应用程序的窗口过程。  
  
## 语法  
  
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
  
#### 参数  
 `lpCreateParams`  
 将与要使用数据的点创建一个窗口。  
  
 `hInstance`  
 识别模块拥有新窗口模块的实例句柄。  
  
 `hMenu`  
 标识新窗口将使用菜单。  子窗口，如果包含整数 ID.  
  
 `hwndParent`  
 标识拥有新窗口的窗口。  新窗口，如果是顶级窗口，该成员是 **NULL**。  
  
 `cy`  
 指定窗口的新高度。  
  
 `cx`  
 指定窗口的新宽度。  
  
 `y`  
 指定新窗口左上角的 y 坐标。  如果新窗口是子窗口，坐标系是相对于父窗口；否则是相对于屏幕坐标原点。  
  
 `x`  
 指定新窗口左上角的 x坐标。  如果新窗口是子窗口，坐标系是相对于父窗口；否则是相对于屏幕坐标原点。  
  
 `style`  
 指定新窗口中 [style](../../mfc/reference/styles-used-by-mfc.md)。  
  
 `lpszName`  
 为指定新窗口的名称以 NULL 结尾的字符串的位置。  
  
 `lpszClass`  
 为指定新窗口的窗口类名的 null 终止的字符串的结构；[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) \(点有关更多信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。\)  
  
 `dwExStyle`  
 对于新窗口指定 [扩展样式](../../mfc/reference/extended-window-styles.md)。  
  
## 要求  
 **头文件：** winuser.h  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../Topic/CWnd::OnCreate.md)