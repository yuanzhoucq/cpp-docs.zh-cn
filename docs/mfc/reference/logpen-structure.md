---
title: "LOGPEN 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LOGPEN
dev_langs: C++
helpviewer_keywords: LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7baf1079fd98213b7d7c3de625d6b39ab6acbf52
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="logpen-structure"></a>LOGPEN 结构
`LOGPEN`结构定义样式、 宽度和钢笔颜色、 图形对象用于绘制线条和边框。 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)函数使用`LOGPEN`结构。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>参数  
 *lopnStyle*  
 指定的钢笔类型。 此成员可以是以下值之一：  
  
- **PS_SOLID**创建实心钢笔。  
  
- **PS_DASH**创建虚线的钢笔。 （仅当钢笔的宽度为 1 时有效）。  
  
- **PS_DOT**创建的以点分隔的钢笔。 （仅当钢笔的宽度为 1 时有效）。  
  
- **PS_DASHDOT**创建具有交替短划线和点的钢笔。 （仅当钢笔的宽度为 1 时有效）。  
  
- **PS_DASHDOTDOT**创建具有交替短划线和双点的钢笔。 （仅当钢笔的宽度为 1 时有效）。  
  
- **PS_NULL**创建 null 钢笔。  
  
- **PS_INSIDEFRAME**创建钢笔绘制由指定边界的矩形的 GDI 输出函数的闭合形状的框架内的行 (例如，**椭圆**，**矩形**， `RoundRect`， `Pie`，和`Chord`成员函数)。 此样式时用于 GDI 输出未指定边界的矩形的函数 (例如，`LineTo`成员函数)，钢笔的绘图区域时不受限制的帧。  
  
     如果钢笔具有**PS_INSIDEFRAME**样式和不匹配逻辑的颜色表中，一种颜色的颜色钢笔绘制抖色的颜色。 **PS_SOLID**笔样式不能用于创建钢笔具有抖色。 **PS_INSIDEFRAME**样式等同于**PS_SOLID**钢笔的宽度是否小于或等于 1。  
  
     当**PS_INSIDEFRAME**样式用于以外生成的函数的 GDI 对象**椭圆**，**矩形**，和`RoundRect`，行可能不完全是在指定范围内。  
  
 *lopnWidth*  
 指定钢笔的宽度，逻辑单位。 如果**lopnWidth**成员为 0，钢笔是 1 个像素宽光栅而不考虑当前的映射模式的设备上。  
  
 *lopnColor*  
 指定的钢笔颜色。  
  
## <a name="remarks"></a>备注  
 **Y**中的值[点](../../mfc/reference/point-structure1.md)结构**lopnWidth**成员未使用。  
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

