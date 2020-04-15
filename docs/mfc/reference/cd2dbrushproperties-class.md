---
title: CD2DBrushProperties 类
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: bf6399d2a245addb7e2e65100d33643fcd54e893
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369291"
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties 类

`D2D1_BRUSH_PROPERTIES`的包装器。

## <a name="syntax"></a>语法

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CD2DBrush 属性：CD2DBrush 属性](#cd2dbrushproperties)|已重载。 创建`CD2D_BRUSH_PROPERTIES`结构|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CD2DBrush 属性：：通用](#commoninit)|初始化对象|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>要求

**标题：** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>CD2DBrush 属性：CD2DBrush 属性

创建CD2D_BRUSH_PROPERTIES结构

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>参数

*_opacity*<br/>
画笔的基本不一性。 默认值为 1.0。

*_transform*<br/>
应用于画笔的转换

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrush 属性：：通用

初始化对象

```
void CommonInit();
```

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
