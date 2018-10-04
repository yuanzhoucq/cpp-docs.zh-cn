---
title: vi_progid （c + + COM 属性） |Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.vi_progid
dev_langs:
- C++
helpviewer_keywords:
- vi_progid attribute
ms.assetid: a52449be-b93e-4111-b883-44bb8da53261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 468b5c5dcadc1715384684062f203ae9179ef044
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2018
ms.locfileid: "48790539"
---
# <a name="viprogid"></a>vi_progid

指定独立于版本的窗体的 ProgID。

## <a name="syntax"></a>语法

```cpp
[ vi_progid(name) ];
```

### <a name="parameters"></a>参数

*name*<br/>
该对象表示独立于版本的 ProgID。

Progid 提供用来标识 COM/ActiveX 对象的类标识符 (CLSID) 的用户可读版本。

## <a name="remarks"></a>备注

**Vi_progid** c + + 属性允许您指定 COM 对象独立于版本的 ProgID。 ProgID 具有窗体*name1.name2.version*。 独立于版本的 ProgID 不具有*版本*。 可以同时指定`progid`并**vi_progid**上的特性`coclass`。 如果未指定**vi_progid**，则独立于版本的 ProgID 是指定的值[progid](progid.md)属性。

**vi_progid**意味着`coclass`属性，也就是说，如果您指定**vi_progid**，它是与指定相同的功能`coclass`并**vi_progid**属性。

**Vi_progid**属性会导致自动注册的指定名称的类。 生成的.idl 文件不会显示进程 Id 值。

在 ATL 项目中，如果[组件类](coclass.md)属性也存在，使用指定的 ProgID`GetVersionIndependentProgID`函数 (由插入`coclass`属性)。

## <a name="example"></a>示例

请参阅[组件类](coclass.md)的示例使用的示例**vi_progid**。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**，**结构**|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参阅[特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[Typedef、Enum、Union 和 Struct 特性](typedef-enum-union-and-struct-attributes.md)<br/>
[类特性](class-attributes.md)<br/>
[ProgID 密钥](/windows/desktop/com/-progid--key)  
