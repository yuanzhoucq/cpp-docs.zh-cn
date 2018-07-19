---
title: MMWORD |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e97b1e58116d633519b1a780928e05862ac1771d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054775"
---
# <a name="mmword"></a>MMWORD
用于 64 位多媒体操作数与 MMX 和 SSE (XMM) 说明。  
  
## <a name="syntax"></a>语法  
  
```  
MMWORD  
```  
  
## <a name="remarks"></a>备注  
 `MMWORD` 是一种类型。  在添加到 MASM MMWORD 之前, 的等效功能可能达到使用：  
  
```  
mov mm0, qword ptr [ebx]  
```  
  
 在这两个说明使用 64 位操作数，同时`QWORD`是 64 位无符号整数的类型和`MMWORD`是 64 位多媒体值的类型。  
  
 `MMWORD` 用于表示与相同的类型[__m64](../../cpp/m64.md)。  
  
## <a name="example"></a>示例  
  
```  
movq     mm0, mmword ptr [ebx]  
```