---
title: XMMWORD |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- XMMWORD
dev_langs:
- C++
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8fd8e6c82a3275161e519eeead490473e8d64ab
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32056413"
---
# <a name="xmmword"></a>XMMWORD
用于 128 位多媒体操作数与 MMX 和 SSE (XMM) 说明。  
  
## <a name="syntax"></a>语法  
  
```  
XMMWORD  
```  
  
## <a name="remarks"></a>备注  
 `XMMWORD` 用于表示与相同的类型[__m128](../../cpp/m128.md)。  
  
## <a name="example"></a>示例  
  
```  
movdqa   xmm0, xmmword ptr [ebx]  
```