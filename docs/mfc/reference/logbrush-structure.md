---
title: LOGBRUSH 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGBRUSH
dev_langs:
- C++
helpviewer_keywords:
- LOGBRUSH structure [MFC]
ms.assetid: 1bf96768-52c5-4444-9bb8-d41ba2e27e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e02c156619e4ca36d268870c70ba783c41a352d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
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
 指定的画笔样式。 `lbStyle`成员必须是以下样式之一：  
  
- **BS_DIBPATTERN**独立于设备的位图 (DIB) 规范所定义的模式画笔。 如果`lbStyle`是**BS_DIBPATTERN**、 **lbHatch**成员包含已打包 DIB 的句柄。  
  
- **BS_DIBPATTERNPT**独立于设备的位图 (DIB) 规范所定义的模式画笔。 如果`lbStyle`是**BS_DIBPATTERNPT**、 **lbHatch**成员包含已打包 DIB 的指针。  
  
- **BS_HATCHED**阴影画笔线。  
  
- **BS_HOLLOW**空心画笔。  
  
- **BS_NULL**相同**BS_HOLLOW**。  
  
- **BS_PATTERN**模式定义的内存位图的画笔。  
  
- **BS_SOLID**实心画笔。  
  
 `lbColor`  
 指定是用要绘制画笔的颜色。 如果`lbStyle`是**BS_HOLLOW**或**BS_PATTERN**样式， **lbColor**将被忽略。 如果`lbStyle`是**BS_DIBPATTERN**或**BS_DIBPATTERNBT**的低序位字**lbColor**指定是否**bmiColors**的成员[BITMAPINFO](../../mfc/reference/bitmapinfo-structure.md)结构到当前已实现的逻辑调色板包含显式的红色、 绿色、 蓝色 (RGB) 值或索引。 **LbColor**成员必须是以下值之一：  
  
- **DIB_PAL_COLORS**颜色表包含的 16 位索引数组到当前已实现的逻辑调色板。  
  
- **DIB_RGB_COLORS**颜色表包含文本的 RGB 值。  
  
 *lbHatch*  
 指定的阴影样式。 含义取决于所定义的画笔样式`lbStyle`。 如果`lbStyle`是**BS_DIBPATTERN**、 **lbHatch**成员包含已打包 DIB 的句柄。 如果`lbStyle`是**BS_DIBPATTERNPT**、 **lbHatch**成员包含已打包 DIB 的指针。 如果`lbStyle`是**BS_HATCHED**、 **lbHatch**成员指定用于创建阴影的行的方向。 它可以是以下值之一：  
  
- `HS_BDIAGONAL` 45 度向上、 从左到右阴影  
  
- `HS_CROSS` 水平和垂直剖面线  
  
- `HS_DIAGCROSS` 45 度剖面线  
  
- `HS_FDIAGONAL` 45 度向下、 从左到右阴影  
  
- `HS_HORIZONTAL` 水平阴影  
  
- `HS_VERTICAL` 垂直阴影  
  
 如果`lbStyle`是**BS_PATTERN**， **lbHatch**是用于定义的模式的位图的句柄。 如果`lbStyle`是**BS_SOLID**或**BS_HOLLOW**， **lbHatch**将被忽略。  
  
## <a name="remarks"></a>备注  
 尽管**lbColor**控制阴影画笔的前景色[CDC::SetBkMode](../../mfc/reference/cdc-class.md#setbkmode)和[CDC::SetBkColor](../../mfc/reference/cdc-class.md#setbkcolor)函数控制的背景色。  
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

