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
ms.openlocfilehash: b15a303f69ce13cf3ba3b6c1c0739acdb8a33c7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309469"
---
# <a name="variant-parameter-type-constants"></a>变量参数类型常量

本主题列出了指示变量参数类型适用于 Microsoft 基础类库的 OLE 控件类的新常量。

下面是一个类常量的列表：

##  <a name="_mfc_variant_data_constants"></a> 变量数据常量

- VTS_COLOR 的 32 位整数，用于表示 RGB 颜色值。

- VTS_FONT 一个指针，指向`IFontDisp`OLE 字体对象接口。

- VTS_HANDLE Windows 句柄值。

- VTS_PICTURE 一个指针，指向`IPictureDisp`OLE 图片对象的接口。

- 打算使用的控件，如单选按钮组中的控件使用 VTS_OPTEXCLUSIVE 的 16 位值。 此类型告知容器，是否一个控件组中的具有值为 TRUE，所有其他用户必须是 FALSE。

- VTS_TRISTATE 的 16 位带符号整数，用于可以有三个可能值之一 （所选、 清除、 不可用），例如，复选框的属性。

- 用于表示的沿 x 轴的位置以 HIMETRIC 为单位 VTS_XPOS_HIMETRIC 的 32 位无符号的整数。

- 用于表示的沿 y 轴的位置以 HIMETRIC 为单位 VTS_YPOS_HIMETRIC 的 32 位无符号的整数。

- 用于表示以像素为单位的沿 x 轴的位置 VTS_XPOS_PIXELS 的 32 位无符号的整数。

- 用于表示以像素为单位的沿 y 轴的位置 VTS_YPOS_PIXELS 的 32 位无符号的整数。

- 用于表示以像素为单位的屏幕对象的宽度 VTS_XSIZE_PIXELS 的 32 位无符号的整数。

- 用于表示以像素为单位的屏幕对象的高度 VTS_YSIZE_PIXELS 的 32 位无符号的整数。

- 用于表示屏幕对象以 HIMETRIC 为单位的宽度 VTS_XSIZE_HIMETRIC 的 32 位无符号的整数。

- 用于表示屏幕对象以 HIMETRIC 为单位的高度 VTS_YSIZE_HIMETRIC 的 32 位无符号的整数。

    > [!NOTE]
    >  其他变体常量已定义的所有变量的类型，除 VTS_FONT 和 VTS_PICTURE，提供变量数据常量的指针。 这些常量使用 VTS_P 命名`constantname`约定。 例如，VTS_PCOLOR 是指向 VTS_COLOR 常量的指针。

## <a name="requirements"></a>要求

**标头：** afxdisp.h

## <a name="see-also"></a>请参阅

[宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)
