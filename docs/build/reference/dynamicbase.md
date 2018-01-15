---
title: "-DYNAMICBASE |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /dynamicbase
dev_langs: C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 07fd3c89cb2cff1fed06189ac66b2e67f7e52ade
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="dynamicbase"></a>/DYNAMICBASE
指定是否可在加载时使用地址空间布局随机化 (ASLR) 功能随机变基可执行映像。  
  
## <a name="syntax"></a>语法  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，链接器设置**/DYNAMICBASE**选项。  
  
 此选项修改可执行映像的标头以指示加载程序是否可以在加载时随机变基映像。  
  
 Windows Vista、Windows Server 2008、Windows 7、Windows 8 和 Windows Server 2012 支持 ASLR。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [Windows ISV 软件安全防御措施](http://msdn.microsoft.com/library/bb430720.aspx)