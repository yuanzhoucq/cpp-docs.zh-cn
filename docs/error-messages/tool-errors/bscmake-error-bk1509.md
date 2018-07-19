---
title: BSCMAKE 错误 BK1509 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1509
dev_langs:
- C++
helpviewer_keywords:
- BK1509
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 825d1e1e119aa80445c5ae15804bbdde4a3d8bf9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295618"
---
# <a name="bscmake-error-bk1509"></a>BSCMAKE 错误 BK1509
堆空间不足  
  
 BSCMAKE 耗尽了内存，包括虚拟内存。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用以下可能的解决方案进行修复  
  
1.  释放一些磁盘空间。  
  
2.  增加交换文件的大小。  
  
3.  增加 Windows 交换文件的大小。  
  
4.  减少的内存使用 /Ei BSCMAKE 要求或者 /Es 以消除一些输入文件或 /Em 以消除宏正文。