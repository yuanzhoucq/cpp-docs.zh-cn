---
title: "/ALLOWBIND | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/allowbind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ALLOWBIND editbin 选项"
  - "/ALLOWBIND editbin 选项"
  - "-ALLOWBIND editbin 选项"
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALLOWBIND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定一个DLL是否可以绑定 。  
  
```  
  
/ALLOWBIND[:NO]  
  
```  
  
## 备注  
 **\/ALLOWBIND** 在 DLL 的头中设置一个位，向 Bind.exe 指示不允许绑定图像。  当加载程序，不必 rebase 和执行每个引用的 DLL 链接地址信息绑定时，的地址可允许图像更快加载。  如果 DLL 已经进行数字签名（绑定使签名无效），可能不需要绑定DLL。  绑定没有效果，则地址空间格式随机化 \(ASLR\) 为图像启用使用在支持 ASLR Windows 版本的 **\/DYNAMICBASE**。  
  
 使用 **\/ALLOWBIND:NO** 防止 Bind.exe 绑定 DLL。  
  
 有关更多信息，请参见 [\/ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md)链接器选项。  
  
## 请参阅  
 [EDITBIN 选项](../../build/reference/editbin-options.md)