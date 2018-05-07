---
title: -ALLOWBIND |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /allowbind
dev_langs:
- C++
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af4a9f3d898d0087f0e8e861ccfe72e4adadb1de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="allowbind"></a>/ALLOWBIND
指定一个 DLL 是否可以绑定。  
  
```  
  
/ALLOWBIND[:NO]  
```  
  
## <a name="remarks"></a>备注  
 **/ALLOWBIND**选项向 Bind.exe 指示允许绑定图像的 DLL 的标头中该位设置设置。 绑定可以允许要在加载程序无需重新设定基址并为每个引用的 DLL 执行地址修正时更快地加载的图像。 您可能不希望如果已进行数字签名绑定 DLL-绑定使签名无效。 绑定如果不起使用映像启用地址空间布局随机化 (ASLR) **/DYNAMICBASE**支持 ASLR 的 Windows 版本上。  
  
 使用 **/allowbind: no**以防止 Bind.exe 绑定 DLL。  
  
 有关详细信息，请参阅[/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)链接器选项。  
  
## <a name="see-also"></a>请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)