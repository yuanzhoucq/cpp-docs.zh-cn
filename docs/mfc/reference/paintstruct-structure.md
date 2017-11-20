---
title: "PAINTSTRUCT 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PAINTSTRUCT
dev_langs: C++
helpviewer_keywords: PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 67be684e04a2ff8d97c58f625f1be39834813b70
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT 结构
`PAINTSTRUCT`结构包含可以用于绘制窗口的客户端区域的信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagPAINTSTRUCT {  
    HDC hdc;  
    BOOL fErase;  
    RECT rcPaint;  
    BOOL fRestore;  
    BOOL fIncUpdate;  
    BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### <a name="parameters"></a>参数  
 *hdc*  
 标识要用于绘制的显示上下文。  
  
 *fErase*  
 指定是否需要重绘背景。 它不是 0，如果应用程序应重绘背景。 应用程序负责绘制背景，如果一个 Windows 窗口类创建无背景画笔 (请参阅说明**hbrBackground**的成员[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)结构在 Windows SDK)。  
  
 *rcPaint*  
 指定的右上角和右下角的顺序请求绘制的矩形。  
  
 *fRestore*  
 保留的成员。 它由 Windows 在内部使用。  
  
 *fIncUpdate*  
 保留的成员。 它由 Windows 在内部使用。  
  
 *rgbReserved [16]*  
 保留的成员。 保留供内部使用 Windows 的内存块。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

