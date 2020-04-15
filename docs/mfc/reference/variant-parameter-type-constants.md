---
title: 变量参数类型常量
ms.date: 11/04/2016
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
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372869"
---
# <a name="variant-parameter-type-constants"></a>变量参数类型常量

本主题列出了新的常量，指示设计用于 Microsoft 基础类库的 OLE 控件类的变体参数类型。

以下是类常量的列表：

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>变体数据常量

- VTS_COLOR 用于表示 RGB 颜色值的 32 位整数。

- VTS_FONT指向 OLE`IFontDisp`字体对象接口的指针。

- VTS_HANDLE Windows 句柄值。

- VTS_PICTURE指向 OLE`IPictureDisp`图片对象的接口的指针。

- VTS_OPTEXCLUSIVE 用于用于一组控件（如单选按钮）中的控件的 16 位值。 此类型告诉容器，如果组中的一个控件具有 TRUE 值，则所有其他控件都必须为 FALSE。

- VTS_TRISTATE 16 位签名整数，用于具有三种可能值之一的属性（选中、清除、不可用），例如复选框。

- VTS_XPOS_HIMETRIC 32 位无符号整数，用于表示在 HIMETRIC 单位中沿 x 轴的位置。

- VTS_YPOS_HIMETRIC 32 位无符号整数，用于表示沿 y 轴的位置（以 HIMETRIC 为单位）。

- VTS_XPOS_PIXELS 32 位无符号整数，用于表示 x 轴沿线的位置（以像素为单位）。

- VTS_YPOS_PIXELS 32 位无符号整数，用于以像素表示沿 y 轴的位置。

- VTS_XSIZE_PIXELS 32 位无符号整数，用于以像素表示屏幕对象的宽度。

- VTS_YSIZE_PIXELS 32 位无符号整数，用于以像素表示屏幕对象的高度。

- VTS_XSIZE_HIMETRIC 用于表示 HIMETRIC 单位屏幕对象的宽度的 32 位无符号整数。

- VTS_YSIZE_HIMETRIC 32 位无符号整数，用于表示 HIMETRIC 单位中的屏幕对象的高度。

    > [!NOTE]
    >  已为所有变体类型定义了其他变体常量，但提供指向变体数据常量的VTS_FONT和VTS_PICTURE除外。 这些常量使用VTS_P`constantname`约定命名。 例如，VTS_PCOLOR是指向VTS_COLOR常量的指针。

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>另请参阅

[MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
