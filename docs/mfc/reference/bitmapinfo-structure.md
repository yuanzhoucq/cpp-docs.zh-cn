---
title: BITMAPINFO 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAPINFO
dev_langs:
- C++
helpviewer_keywords:
- BITMAPINFO structure [MFC]
ms.assetid: a00caa49-e4df-419f-89a7-ab03c13a1b5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e061802cbcd8926a146e5765cc9ecfd9bf917295
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO 结构
`BITMAPINFO`结构定义的维度和 Windows 设备独立位图 (DIB) 的颜色信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>参数  
 `bmiHeader`  
 指定[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)结构，它包含的维度和独立于设备的位图的颜色格式有关的信息。  
  
 `bmiColors`  
 指定的数组[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)或`DWORD`在位图中定义的颜色的数据类型。  
  
## <a name="remarks"></a>备注  
 独立于设备的位图包含两个不同部分：`BITMAPINFO`说明的维度和颜色位图，并指定在位图中的像素为单位的字节数组的结构。 数组中的位打包在一起，但每个扫描行必须填充了零以上结束`LONG`边界。 如果正高度的源位图的是左下角。 如果高度为负，是的左上角的起点。  
  
 A*已打包的位图*是位图的字节数组紧随`BITMAPINFO`结构。 由单个指针引用已打包的位图。  
  
 有关详细信息`BITMAPINFO`结构和相应的成员的值`BITMAPINFOHEADER`和`RGBQUAD`结构，请参阅 Windows SDK 文档中的以下主题。  
  
- [BITMAPINFO 结构](http://msdn.microsoft.com/library/windows/desktop/dd183375)  
  
- [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)结构  
  
- [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)结构  
  
## <a name="requirements"></a>要求  
 **标头：** wingdi.h  
  
## <a name="see-also"></a>请参阅  
 [结构、 样式、 回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CBrush::CreateDIBPatternBrush](../../mfc/reference/cbrush-class.md#createdibpatternbrush)   
 [BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)   
 [RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)

