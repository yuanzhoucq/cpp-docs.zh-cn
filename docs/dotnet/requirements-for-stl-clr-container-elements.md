---
title: "STL/CLR 容器元素的要求 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, template class containers
- STL/CLR, containers
- containers, STL/CLR
- containers, C++ Standard Library
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3317e3c9349963fc24b37b421def05c475732fd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="requirements-for-stlclr-container-elements"></a>STL/CLR 容器元素的需求
插入 STL/CLR 容器的所有引用类型必须至少具有以下元素：  
  
-   公共复制构造函数。  
  
-   公共赋值运算符。  
  
-   公共析构函数。  
  
 此外，如的关联容器[设置](../dotnet/set-stl-clr.md)和[映射](../dotnet/map-stl-clr.md)必须具有公共比较运算符定义，即`operator<`默认情况下。 对容器的某些运算还可能需要定义公共默认构造函数和公共等效运算符。  
  
 与引用类型相似，要插入关联容器的引用类型的值类型和句柄必须有一个比较运算符，如 `operator<`。 引用类型的值类型或句柄没有对公共复制构造函数、公共赋值运算符和公共析构函数的需求。  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)