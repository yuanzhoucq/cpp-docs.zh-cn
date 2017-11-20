---
title: "编译器错误 C3138 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3138
dev_langs: C++
helpviewer_keywords: C3138
ms.assetid: 364ee9e8-9358-410e-bd35-9c4a226a3753
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ba06bed1ce02c8a3030720152892e0e35760afa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3138"></a>编译器错误 C3138
interface: attribute 接口必须继承从 IDispatch，或从 IDispatch 继承的接口  
  
 与接口[双重](../../windows/dual.md)或[调度接口](../../windows/dispinterface.md)属性不具有`IDispatch`为直接或间接基接口。  
  
 下面的示例生成 C3138:  
  
```  
// C3138.cpp  
#include <unknwn.h>  
  
[ object, uuid("77ac9240-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyCustomInterface  
{  
   HRESULT mf1(void);  
};  
  
[ dispinterface, uuid("3536f8a0-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyDispInterface : IUnknown  
{  
   [id(1)] HRESULT mf2(void);  
};  
  
[ object, dual, uuid("34e90a10-6e9a-11d2-97de-0000f805d73b") ]  
__interface IMyDualInterface : IMyCustomInterface  // C3138 expected  
{  
   HRESULT mf3(void);  
};  
```