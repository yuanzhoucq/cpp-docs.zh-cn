---
title: 'Platform:: delegate 类 |Microsoft 文档'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
dev_langs:
- C++
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 679a868cac536aad541d770433fe1407fc5d08d1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="platformdelegate-class"></a>Platform::Delegate 类
表示函数对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public delegate void delegate_name();  
```  
  
### <a name="members"></a>成员  
 Delegate 类具有从 [Platform::Object Class](../cppcx/platform-object-class.md)派生的 Equals()、GetHashCode() 和 ToString() 方法。  
  
### <a name="remarks"></a>备注  
 使用 [delegate](../windows/delegate-cpp-component-extensions.md) 关键字创建委托；不要显式使用 Platform::Delegate。 有关详细信息，请参阅[委托](../cppcx/delegates-c-cx.md)。 有关如何创建和使用委托的示例，请参阅[创建 Windows 运行时 c + + 组件](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)。  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform  
  
 **元数据：** platform.winmd  
  
## <a name="see-also"></a>请参阅  
 [平台命名空间](../cppcx/platform-namespace-c-cx.md)