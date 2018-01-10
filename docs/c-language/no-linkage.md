---
title: "无链接 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: abacc6fbd49f9f42620385a4206c9412648c173b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="no-linkage"></a>无链接
如果块内的某个标识符的声明不包括 `extern` 存储类说明符，则该标识符没有链接并且对函数是唯一的。  
  
 以下标识符没有链接：  
  
-   声明为除对象或函数以外的任何项的标识符  
  
-   声明为函数参数的标识符  
  
-   声明时未使用 `extern` 存储类说明符的对象的块范围标识符  
  
 如果标识符没有链接，那么在相同的范围级别内再次声明相同的名称（在声明符或类型说明符中）将产生符号重新定义错误。  
  
## <a name="see-also"></a>请参阅  
 [使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)