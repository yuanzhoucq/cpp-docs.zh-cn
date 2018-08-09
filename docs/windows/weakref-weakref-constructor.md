---
title: 'Weakref:: Weakref 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eafbddea6ae651d74d8f33be8efa58c25a8a0d3d
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641468"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef 构造函数
初始化的新实例**WeakRef**类。  
  
## <a name="syntax"></a>语法  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
### <a name="parameters"></a>参数  
 *ptr*  
 指针、 引用或对现有对象的初始化当前的右值引用**WeakRef**对象。  
  
## <a name="remarks"></a>备注  
 第一个构造函数会初始化一个空**WeakRef**对象。 第二个构造函数初始化**WeakRef**对象从指针到`IWeakReference`接口。 第三个构造函数初始化**WeakRef**对象从引用到`ComPtr<IWeakReference>`对象。 第四个和第五个构造函数初始化**WeakRef**从另一个对象**WeakRef**对象。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [WeakRef 类](../windows/weakref-class.md)