---
title: 'Module:: unregisterobjects 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::UnregisterObjects
dev_langs:
- C++
helpviewer_keywords:
- UnregisterObjects method
ms.assetid: 3d8119a7-991d-45e9-b8c5-ed36c0be0332
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 87fb8ece3e1897a3ba460403d273bd649784ad44
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400417"
---
# <a name="moduleunregisterobjects-method"></a>Module::UnregisterObjects 方法

取消指定模块中的对象，以便其他应用程序无法连接到它们。

## <a name="syntax"></a>语法

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>参数

*模块*<br/>
指向模块的指针。

*服务器名称*<br/>
指定受此操作影响的对象子集的限定名。

## <a name="return-value"></a>返回值

如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)