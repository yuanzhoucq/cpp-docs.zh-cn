---
title: "Module::GenericReleaseNotifier::GenericReleaseNotifier 构造函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::Module::GenericReleaseNotifier::GenericReleaseNotifier
dev_langs: C++
helpviewer_keywords: GenericReleaseNotifier, constructor
ms.assetid: feb5b687-a4b0-4809-9022-8f292181b7a1
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f0309040b64614280d2314daa83c5919514b3fb6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="modulegenericreleasenotifiergenericreleasenotifier-constructor"></a>Module::GenericReleaseNotifier::GenericReleaseNotifier 构造函数
初始化 Module::GenericReleaseNotifier 类的新实例。  
  
## <a name="syntax"></a>语法  
  
```  
  
      GenericReleaseNotifier(  
   T callback,   
   bool release  
) throw() : ReleaseNotifier(release), callback_(callback);  
```  
  
#### <a name="parameters"></a>参数  
 `callback`  
 Lambda、 functor 或指针函数事件处理程序可以使用括号函数运算符调用 (`()`)。  
  
 `release`  
 指定`true`以便调用基础[模块:: ReleaseNotifier::Release()](../windows/module-releasenotifier-release.md)方法; 否则，指定`false`。  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>另请参阅  
 [Module::GenericReleaseNotifier 类](../windows/module-genericreleasenotifier-class.md)