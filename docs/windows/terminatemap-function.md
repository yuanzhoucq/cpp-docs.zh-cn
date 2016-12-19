---
title: "TerminateMap 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::TerminateMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TerminateMap 函数"
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TerminateMap 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
inline bool TerminateMap(  
   _In_ ModuleBase *module,   
   _In_opt_z_ const wchar_t *serverName,   
    bool forceTerminate) throw()  
```  
  
## <a name="parameters"></a>参数  
 `module`  
 一个 [模块](../windows/module-class.md)。  
  
 `serverName`  
 由参数指定的模块中类工厂的子集名称 `module`。  
  
 `forceTerminate`  
 `true` 若要终止类工厂，而不考虑它们处于活动状态; `false` 不终止类工厂，如果任何工厂处于活动状态。  
  
## <a name="return-value"></a>返回值  
 `true` 如果所有的类工厂已终止;否则为 `false`。  
  
## <a name="remarks"></a>备注  
 关闭指定的模块中的类工厂。  
  
## <a name="requirements"></a>要求  
 **标头︰** module.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另请参阅  
 [Microsoft::WRL::Details Namespace](../windows/microsoft-wrl-details-namespace.md)