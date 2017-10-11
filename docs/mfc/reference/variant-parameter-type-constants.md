---
title: "变量参数类型常量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
dev_langs:
- C++
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 4a770b6508067913aec51b8b3878f33e30eed4bb
ms.openlocfilehash: cc8daf0853a97e8903b47d29f70e190430931fd5
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="variant-parameter-type-constants"></a>变量参数类型常量
本主题列出指示变量参数类型适用于 Microsoft 基础类库 OLE 控件类的新常量。  
  
 下面是一个类常量的列表：  
  
##  <a name="_mfc_variant_data_constants"></a>变量数据常量  
  
-   **VTS_COLOR**用于表示 RGB 颜色值的 32 位整数。  
  
-   **VTS_FONT**指向的指针**IFontDisp** OLE 字体对象接口。  
  
-   **VTS_HANDLE** Windows 句柄值。  
  
-   **VTS_PICTURE**指向的指针`IPictureDisp`OLE 图片对象的接口。  
  
-   **VTS_OPTEXCLUSIVE**用于旨在用于一组控件，如单选按钮的控件的 16 位值。 此类型通知容器，如果其中一个控制在一个组具有**TRUE**值，其他所有类型必须为**FALSE**。  
  
-   **VTS_TRISTATE** 16 位有符号的整数用于属性可以有一个三个可能的值 （所选、 清除、 不可用），例如，复选框。  
  
-   **VTS_XPOS_HIMETRIC**的 32 位无符号的整数，用于表示沿 x 轴中的位置**HIMETRIC**单位。  
  
-   **VTS_YPOS_HIMETRIC**的 32 位无符号的整数，用于表示在 y 轴上的位置**HIMETRIC**单位。  
  
-   **VTS_XPOS_PIXELS**的 32 位无符号的整数，用于表示沿 x 轴以像素为单位的位置。  
  
-   **VTS_YPOS_PIXELS**的 32 位无符号的整数，用于表示沿 y 轴以像素为单位的位置。  
  
-   **VTS_XSIZE_PIXELS**的 32 位无符号的整数，用于表示以像素为单位的屏幕对象的宽度。  
  
-   **VTS_YSIZE_PIXELS**的 32 位无符号的整数，用于表示以像素为单位的屏幕对象的高度。  
  
-   **VTS_XSIZE_HIMETRIC**的 32 位无符号的整数，用于表示中的屏幕对象的宽度**HIMETRIC**单位。  
  
-   **VTS_YSIZE_HIMETRIC**的 32 位无符号的整数，用于表示中的屏幕对象的高度**HIMETRIC**单位。  
  
    > [!NOTE]
    >  为所有变体类型，除定义其他变体常量**VTS_FONT**和**VTS_PICTURE**，提供指向各种不同的数据产生的 constant。 使用命名这些常量**VTS_P** `constantname`约定。 例如， **VTS_PCOLOR**是一个指向**VTS_COLOR**常量。  
  
## <a name="requirements"></a>要求  
 **标头：** afxdisp.h  
  
## <a name="see-also"></a>另请参阅  
 [宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)

