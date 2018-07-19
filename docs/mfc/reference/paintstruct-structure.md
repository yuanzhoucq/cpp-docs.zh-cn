---
title: PAINTSTRUCT 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75a3db6c6beb18afe2303b464fcab290b2e132fc
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338205"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT 结构
`PAINTSTRUCT`结构包含可用于绘制的窗口工作区的信息。  
  
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
 指定是否需要重新绘制背景。 它不是 0，如果应用程序应重绘后台。 应用程序负责绘制背景，如果没有背景画笔的情况下创建一个 Windows 窗口类 (请参阅的说明`hbrBackground`的成员[WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) Windows SDK 中的结构)。  
  
 *rcPaint*  
 指定右上角和右下角的绘制请求在其中的矩形。  
  
 *fRestore*  
 保留的成员。 它是由 Windows 在内部使用。  
  
 *fIncUpdate*  
 保留的成员。 它是由 Windows 在内部使用。  
  
 *rgbReserved [16]*  
 保留的成员。 保留的由 Windows 在内部使用的内存块。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

