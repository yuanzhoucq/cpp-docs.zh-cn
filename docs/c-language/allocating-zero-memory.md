---
title: "分配零内存 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 05d05cefb6b35d4272c0e0e6fee29205de063fd4
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="allocating-zero-memory"></a>分配零内存
**ANSI 4.10.3** 请求的大小为零时，`calloc`、`malloc` 或 `realloc` 函数的行为  
  
 `calloc`、`malloc` 和 `realloc` 函数接受零作为参数。 不分配实际内存，但会返回有效的指针，并且之后可通过 realloc 修改内存块。  
  
## <a name="see-also"></a>另请参阅  
 [库函数](../c-language/library-functions.md)
