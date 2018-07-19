---
title: BITMAPINFO 结构 |Microsoft Docs
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
ms.openlocfilehash: a9b1bd896157d7f11792a5a6514e30ecd3d46a19
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37336252"
---
# <a name="bitmapinfo-structure"></a>BITMAPINFO 结构
`BITMAPINFO`结构定义的维度和 Windows 设备无关位图 (DIB) 的颜色信息。  
  
## <a name="syntax"></a>语法  
  
```  
typedef struct tagBITMAPINFO {  
    BITMAPINFOHEADER bmiHeader;  
    RGBQUAD bmiColors[1];  
} BITMAPINFO;  
```  
  
#### <a name="parameters"></a>参数  
 *bmiHeader*  
 指定[BITMAPINFOHEADER](http://msdn.microsoft.com/library/windows/desktop/dd183376)结构，其中包含有关维度和独立于设备的位图的颜色格式信息。  
  
 *bmiColors*  
 指定的数组[RGBQUAD](http://msdn.microsoft.com/library/windows/desktop/dd162938)或位图中定义的颜色的 DWORD 数据类型。  
  
## <a name="remarks"></a>备注  
 与设备无关位图包含两个不同部分：`BITMAPINFO`说明的维度和颜色位图，并指定像素的位图中的字节数组的结构。 数组中的位将打包在一起，但每个扫描行必须填充了零以结束**长**边界。 如果高度为正，位图的源是左下角。 高度为负，如果源是左上角。  
  
 一个*打包的位图*是一个位图，其中的字节数组紧随`BITMAPINFO`结构。 由单个指针引用已打包的位图。  
  
 有关详细信息`BITMAPINFO`结构，并将相应值的成员`BITMAPINFOHEADER`和`RGBQUAD`结构，请参阅 Windows SDK 文档中的以下主题。  
  
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

