---
title: "Module::ReleaseNotifier::ReleaseNotifier 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::ReleaseNotifier::ReleaseNotifier
dev_langs: C++
helpviewer_keywords: ReleaseNotifier, constructor
ms.assetid: 889a3c9a-2366-44a1-ba7d-a59c1885e7f3
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81d4f136fc9982b7260ce08d3fca4e9037f60c22
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="modulereleasenotifierreleasenotifier-constructor"></a>Module::ReleaseNotifier::ReleaseNotifier 构造函数
初始化 Module::ReleaseNotifier 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
ReleaseNotifier(bool release) throw();  
```  
  
#### <a name="parameters"></a>参数  
 `release`  
 `true`若要删除此实例时调用 Release 方法;`false`不删除此实例。  
  
## <a name="exceptions"></a>异常  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)