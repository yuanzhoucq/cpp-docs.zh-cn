---
title: "编译器错误 C3141 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3141
dev_langs: C++
helpviewer_keywords: C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f04c8f1a7772b202060de132693473a98ba26215
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3141"></a>编译器错误 C3141
interface_name： 接口只支持公共继承  
  
 使用定义的接口[接口 （或 __interface）](../../cpp/interface.md)关键字仅支持公共继承。  
  
 下面的示例生成 C3141:  
  
```  
// C3141.cpp  
__interface IBase {};  
__interface IDerived1 : protected IBase {};  // C3141  
__interface IDerived2 : private IBase {};    // C3141  
```