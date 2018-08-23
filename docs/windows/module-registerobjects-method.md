---
title: 'Module:: registerobjects 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::RegisterObjects
dev_langs:
- C++
helpviewer_keywords:
- RegisterObjects method
ms.assetid: db4077b7-068d-4534-aaa5-41b5444ccb49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c9a44fed853fe2f4dcd3196e926b3848566ab4e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597021"
---
# <a name="moduleregisterobjects-method"></a>Module::RegisterObjects 方法

注册 COM 或 Windows 运行时对象，以便其他应用程序可以连接到它们。

## <a name="syntax"></a>语法

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>参数

*模块*  
COM 或 Windows 运行时对象的数组。

*服务器名称*  
创建对象的服务器的名称。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Module 类](../windows/module-class.md)