---
title: "编译器错误 C3340 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3340
dev_langs: C++
helpviewer_keywords: C3340
ms.assetid: 23b12298-b92a-4717-8380-f165c998cb8a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 80eb5ea3cfb4ba0a415a1ee188b13a82e03b9dea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3340"></a>编译器错误 C3340
“interface”：组件类“class”中的接口不能同时是“restricted”和“default”  
  
 [restricted](../../windows/restricted.md) 特性和 [default](../../windows/default-cpp.md) 特性是互相排斥的。  
  
 下面的示例生成 C3340：  
  
```  
// C3340.cpp  
#include <windows.h>  
[module(name="MyModule")];  
  
[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]  
__interface IMyIface  
{  
   HRESULT f1();  
};  
  
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f),  
default(IMyIface),  
source(IMyIface),restricted(IMyIface) ]  
class CmyClass // C3340  
{  
};  
  
int main()  
{  
}  
```