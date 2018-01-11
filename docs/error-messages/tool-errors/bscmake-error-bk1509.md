---
title: "BSCMAKE 错误 BK1509 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1509
dev_langs: C++
helpviewer_keywords: BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e4d5fe0a83c5fbc3c4793699975d2045df5fbd8f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 错误 BK1509
堆空间不足  
  
 BSCMAKE 耗尽了内存，包括虚拟内存。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  释放一些磁盘空间。  
  
2.  增加交换文件的大小。  
  
3.  增加 Windows 交换文件的大小。  
  
4.  减少的内存使用 /Ei BSCMAKE 要求或者 /Es 以消除一些输入文件或 /Em 以消除宏正文。