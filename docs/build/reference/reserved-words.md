---
title: "保留字 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35f9a3e907b72b4b8cf8e673e771832ba3fc0527
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="reserved-words"></a>保留字
链接器将保留下列词语。 这些名称可用作自变量中[模块定义语句](../../build/reference/module-definition-dot-def-files.md)仅当名称括在双引号 ("")。  
  
||||  
|-|-|-|  
|**APPLOADER**1|**INITINSTANCE**2|**预加载**|  
|**基**|**IOPL**|**私有**|  
|**代码**|**库**1|**PROTMODE**2|  
|**符合**|**由**1|**纯**1|  
|**数据**|**LONGNAMES**2|**READONLY**|  
|**说明**|**可移动**1|**READWRITE**|  
|**DEV386**|**可移动**1|**实模式**1|  
|**可丢弃**|**多个**|**驻留**|  
|**动态**|**名称**|**RESIDENTNAME**1|  
|**仅执行**|**NEWFILES**2|**部分**|  
|**EXECUTEONLY**|**无数据**1|**段**|  
|**执行读取**|**NOIOPL**1|**共享**|  
|**EXETYPE**|**NONAME**|**单个**|  
|**EXPORTS**|**不一致性**1|**STACKSIZE**|  
|**固定**1|**NONDISCARDABLE**|**STUB**|  
|**函数**2|**无**|**版本**|  
|**HEAPSIZE**|**非共享**|**WINDOWAPI**|  
|**导入**|**NOTWINDOWCOMPAT**1|**WINDOWCOMPAT**|  
|**非纯**1|**对象**|**WINDOWS**|  
|**包括**2|**旧**1||  
  
 1 当它遇到此术语，链接器将发出警告 （"忽略"）。 但是，单词是仍保留。  
  
 2 链接器忽略该保留字，但是不发出警告。  
  
## <a name="see-also"></a>请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)