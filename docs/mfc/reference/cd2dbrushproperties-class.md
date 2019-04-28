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
ms.openlocfilehash: 5ca791af658ee719b2e6d6ea78f82e23a66edc98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253712"
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties 类

`D2D1_BRUSH_PROPERTIES`的包装器。

## <a name="syntax"></a>语法

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|已重载。 创建`CD2D_BRUSH_PROPERTIES`结构|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|初始化对象|

## <a name="inheritance-hierarchy"></a>继承层次结构

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>要求

**标头：** afxrendertarget.h

##  <a name="cd2dbrushproperties"></a>  CD2DBrushProperties::CD2DBrushProperties

创建 CD2D_BRUSH_PROPERTIES 结构

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>参数

*_opacity*<br/>
基不透明度的画笔。 默认值为 1.0。

*_transform*<br/>
要应用到画笔的转换

##  <a name="commoninit"></a>  CD2DBrushProperties::CommonInit

初始化对象

```
void CommonInit();
```

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
