---
title: -DYNAMICBASE |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /dynamicbase
dev_langs:
- C++
helpviewer_keywords:
- -DYNAMICBASE editbin option
- DYNAMICBASE editbin option
- /DYNAMICBASE editbin option
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d7a4cf7aa35d7ad6b41fc6d61f3f27662ae2c8d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="dynamicbase"></a>/DYNAMICBASE
指定是否可在加载时使用地址空间布局随机化 (ASLR) 功能随机变基可执行映像。  
  
## <a name="syntax"></a>语法  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## <a name="remarks"></a>备注  
 默认情况下，链接器设置 **/DYNAMICBASE**选项。  
  
 此选项修改可执行映像的标头以指示加载程序是否可以在加载时随机变基映像。  
  
 Windows Vista、Windows Server 2008、Windows 7、Windows 8 和 Windows Server 2012 支持 ASLR。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)   
 [Windows ISV 软件安全防御措施](http://msdn.microsoft.com/library/bb430720.aspx)