---
title: "编译器错误 C3099 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3099
dev_langs: C++
helpviewer_keywords: C3099
ms.assetid: b3dded0f-76c9-42c1-991b-532eb8619661
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a644a27c834efcd3c3857241927a6e618f600d0c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3099"></a>编译器错误 C3099
“关键字”：将 [System::AttributeUsageAttribute] 用于托管特性；将 [Windows::Foundation::Metadata::AttributeUsageAttribute] 用于 WinRT 特性  
  
 使用<xref:System.AttributeUsageAttribute>声明**/clr**属性。 使用 `Windows::Foundation::Metadata::AttributeUsageAttribute` 声明 Windows 运行时特性。  
  
 有关 /CLR 特性的详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。 有关受支持 Windows 运行时中的属性，请参阅[Windows.Foundation.Metadata 命名空间](http://msdn.microsoft.com/library/windows/apps/windows.foundation.metadata.aspx)  
  
## <a name="example"></a>示例  
 下面的示例生成 C3099，并演示如何修复此错误。  
  
```  
// C3099.cpp  
// compile with: /clr /c  
using namespace System;  
[usage(10)]   // C3099  
// try the following line instead  
// [AttributeUsageAttribute(AttributeTargets::All)]  
ref class A : Attribute {};  
```