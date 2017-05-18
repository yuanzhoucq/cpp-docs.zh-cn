---
title: "LOGBRUSH 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
caps.latest.revision: 11
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: eea7caf6139fd43dd77163271701d170c7a744e2
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="logbrush-structure"></a>LOGBRUSH 结构
`LOGBRUSH`结构定义样式、 颜色和模式的物理画笔。 它由 Windows [CreateBrushIndirect](http://msdn.microsoft.com/library/windows/desktop/dd183487)和[ExtCreatePen](http://msdn.microsoft.com/library/windows/desktop/dd162705)函数。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tag LOGBRUSH { /* lb */  
    UINT lbStyle;  
    COLORREF lbColor;  
    LONG lbHatch;  
} LOGBRUSH;  
```  
  
#### <a name="parameters"></a>参数  
 `lbStyle`  
 指定画笔样式。 `lbStyle`成员必须为下列样式之一︰  
  
- **BS_DIBPATTERN**图案画笔与设备无关位图 (DIB) 规范所定义的。 如果`lbStyle`是**BS_DIBPATTERN**、 **lbHatch**成员将包含打包 DIB 的句柄。  
  
- **BS_DIBPATTERNPT**图案画笔与设备无关位图 (DIB) 规范所定义的。 如果`lbStyle`是**BS_DIBPATTERNPT**、 **lbHatch**成员包含一个已打包 DIB 的指针。  
  
- **BS_HATCHED**影线画笔。  
  
- **BS_HOLLOW**空心画笔。  
  
- **BS_NULL**相同**BS_HOLLOW**。  
  
- **BS_PATTERN**模式由内存位图定义画笔。  
  
- **BS_SOLID**实心画笔。  
  
 `lbColor`  
 指定是用来绘制画笔的颜色。 如果`lbStyle`是**BS_HOLLOW**或**BS_PATTERN**样式， **lbColor**将被忽略。 如果`lbStyle`是**BS_DIBPATTERN**或**BS_DIBPATTERNBT**的低位字**lbColor**指定是否**bmiColors**成员[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)结构包含显式 red、 green、 蓝 (RGB) 值或索引当前已实现的逻辑调色板。 **LbColor**成员必须为下列值之一︰  
  
- **DIB_PAL_COLORS**颜色表由 16 位索引的数组构成当前已实现的逻辑调色板。  
  
- **DIB_RGB_COLORS**颜色表包含文本的 RGB 值。  
  
 *lbHatch*  
 指定阴影样式。 其含义取决于所定义的画笔样式`lbStyle`。 如果`lbStyle`是**BS_DIBPATTERN**、 **lbHatch**成员将包含打包 DIB 的句柄。 如果`lbStyle`是**BS_DIBPATTERNPT**、 **lbHatch**成员包含一个已打包 DIB 的指针。 如果`lbStyle`是**BS_HATCHED**、 **lbHatch**成员指定用于创建阴影的行的方向。 它可以是下列值之一︰  
  
- `HS_BDIAGONAL`45 度呈上升趋势、 从左到右阴影  
  
- `HS_CROSS`水平和垂直交叉影线  
  
- `HS_DIAGCROSS`45 度交叉影线  
  
- `HS_FDIAGONAL`45 度向下、 从左到右阴影  
  
- `HS_HORIZONTAL`水平阴影  
  
- `HS_VERTICAL`垂直阴影  
  
 如果`lbStyle`是**BS_PATTERN**， **lbHatch**是定义的模式的位图的句柄。 如果`lbStyle`是**BS_SOLID**或**BS_HOLLOW**， **lbHatch**将被忽略。  
  
## <a name="remarks"></a>备注  
 尽管**lbColor**控制阴影画笔的前景色[CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode)和[CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor)函数控制的背景色。  
  
## <a name="requirements"></a>要求  
 **标头︰** wingdi.h  
  
## <a name="see-also"></a>另请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


