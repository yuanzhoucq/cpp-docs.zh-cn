---
title: 'Module:: module 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Module
dev_langs:
- C++
helpviewer_keywords:
- Module, constructor
ms.assetid: 5436fc74-61dc-41b6-81af-4f03177159aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b31e9f1e4536bc124bba359ece10217ef8b7f253
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875248"
---
# <a name="modulemodule-constructor"></a>Module::Module 构造函数
初始化 Module 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
Module();  
```  
  
## <a name="remarks"></a>备注  
 此构造函数受保护，不能使用 `new` 关键字进行调用。 相反，调用[module:: getmodule 方法](../windows/module-getmodule-method.md)或[module:: create 方法](../windows/module-create-method.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [Module 类](../windows/module-class.md)