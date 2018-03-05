---
title: "依赖项的搜索路径 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, dependents
- dependents, NMAKE
ms.assetid: bf998e47-da74-48b5-891d-d3d8ce57264b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f6093db4ac8e0c88dfe6e4b5a5463e5ee8d24349
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="search-paths-for-dependents"></a>依赖项的搜索路径
每个依赖项有一个可选的搜索路径，指定，如下所示：  
  
## <a name="syntax"></a>语法  
  
```  
{directory[;directory...]}dependent  
```  
  
## <a name="remarks"></a>备注  
 NMAKE 中寻找的依赖项首先在当前目录中，然后在指定的顺序的目录。 宏可以指定部分或全部的搜索路径。 将目录名称括在大括号 （{}）;使用分号 （;） 分隔多个目录。 不允许任何空格或制表符。  
  
## <a name="see-also"></a>请参阅  
 [依赖项](../build/dependents.md)