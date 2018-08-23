---
title: 编译器警告 （等级 1） C4096 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3787ef5482841e33658e02371fa0f6d1682612ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276274"
---
# <a name="compiler-warning-level-1-c4096"></a>编译器警告 （等级 1） C4096
a： 接口不是一个 COM 接口;不会发出到 IDL  
  
 你可能应为 COM 接口的接口定义未被定义为 COM 接口，因此将不会发送到 IDL 文件。  
  
 请参阅[接口属性](../../windows/interface-attributes.md)指示接口是一个 COM 接口的列表属性。  
  
 下面的示例生成 C4096:  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```