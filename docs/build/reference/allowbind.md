---
title: "-ALLOWBIND |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a4cbd5c619b0a9e146adb9a8ec9117f59e01b89d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="allowbind"></a>/ALLOWBIND
指定一个 DLL 是否可以绑定。  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>备注  
 **/ALLOWBIND**选项向 Bind.exe 指示允许绑定图像的 DLL 的标头中该位设置设置。 绑定可以允许要在加载程序无需重新设定基址并为每个引用的 DLL 执行地址修正时更快地加载的图像。 您可能不希望如果已进行数字签名绑定 DLL-绑定使签名无效。 绑定如果不起使用映像启用地址空间布局随机化 (ASLR) **/DYNAMICBASE**支持 ASLR 的 Windows 版本上。  
  
 使用**/allowbind: no**以防止 Bind.exe 绑定 DLL。  
  
 有关详细信息，请参阅[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)链接器选项。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)