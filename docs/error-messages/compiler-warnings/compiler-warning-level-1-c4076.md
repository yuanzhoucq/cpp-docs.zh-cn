---
title: 编译器警告 （等级 1） C4076 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4076
dev_langs:
- C++
helpviewer_keywords:
- C4076
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 928b0a78c09773e334c1a291877b74304dab66ec
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198473"
---
# <a name="compiler-warning-level-1-c4076"></a>编译器警告（等级 1）C4076

> '*的类型修饰符*： 不能使用类型*typename*

## <a name="remarks"></a>备注

类型修饰符，它是否**签名**或**无符号**，不能用于非整数类型。 *类型修饰符*将被忽略。
  
## <a name="example"></a>示例  

下面的示例生成 C4076;若要修复此错误，请删除**无符号**类型修饰符：

```cpp
// C4076.cpp  
// compile with: /W1 /LD  
unsigned double x;   // C4076  
```