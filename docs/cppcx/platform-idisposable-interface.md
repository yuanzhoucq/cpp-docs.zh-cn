---
title: 'Platform:: idisposable 接口 |Microsoft 文档'
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 68c5425d5d65acc194287a97068df7da15f37275
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33086963"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable 接口
用于释放非托管资源。  
  
## <a name="syntax"></a>语法  
  
```cpp  
public interface class IDisposable  
```  
  
## <a name="attributes"></a>特性  
 **GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")  
  
 **VersionAttribute**(NTDDI_WIN8)  
  
### <a name="members"></a>成员  
 IDisposable 接口从 IUnknown 接口继承。 IDisposable 还具有下列类型的成员：  
  
 **方法**  
  
 IDisposable 接口具有以下方法。  
  
|方法|描述|  
|------------|-----------------|  
|释放|用于释放非托管资源。|  
  
### <a name="requirements"></a>要求  
 **支持的最低客户端：** Windows 8  
  
 **支持的最低服务器：** Windows Server 2012  
  
 **命名空间：** Platform