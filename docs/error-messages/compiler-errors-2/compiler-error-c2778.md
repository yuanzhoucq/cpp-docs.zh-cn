---
title: 编译器错误 C2778 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2778
dev_langs:
- C++
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d68180e2fc0c7c33e742f0ffdb3776baa50976f6
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209708"
---
# <a name="compiler-error-c2778"></a>编译器错误 C2778
在 __declspec(uuid()) GUID 格式不正确  
  
 不正确的 GUID 提供给[uuid](../../cpp/uuid-cpp.md)扩展的特性。  
  
 GUID 必须为具有以下格式的十六进制数字的字符串：  
  
```  
// C2778a.cpp  
// compile with: /c  
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};  
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};  
```  
  
 `uuid`扩展的特性接受字符串识别[CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring)、 使用或不带括号分隔符。  
  
 下面的示例生成 C2778:  
  
```  
// C2778b.cpp  
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778  
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778  
```