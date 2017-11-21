---
title: "Platform:: idisposable 接口 |Microsoft 文档"
ms.custom: 
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: VCCORLIB/Platform::IDisposable
dev_langs: C++
helpviewer_keywords: Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
caps.latest.revision: "4"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 0bc36087532bbac86b5891408fc3e4bea30c0256
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
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