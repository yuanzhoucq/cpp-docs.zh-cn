---
title: 'Ftmbase:: Getunmarshalclass 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 167ad8537a11a0118c15b588b353f33775b5ab3a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644994"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass 方法
获取 COM 用来定位相应代理包含代码的 DLL 的 CLSID。 COM 加载此 DLL 才能创建代理的未初始化的实例。  
  
## <a name="syntax"></a>语法  
  
```cpp  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
### <a name="parameters"></a>参数  
 *riid*  
 引用封送的接口标识符。  
  
 *pv*  
 指向要封送处理; 的接口如果调用方不具有到所需的接口指针，则可以为 NULL。  
  
 *dwDestContext*  
 其中将被取消封送指定的接口的目标上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 在当前进程 (MSHCTX_INPROC) 的另一单元中或作为当前进程 (MSHCTX_LOCAL) 在同一台计算机上的另一个进程中，可能发生取消封送。  
  
 *pvDestContext*  
 保留供将来使用;必须为 NULL。  
  
 *mshlflags*  
 此操作完成后，若要使用客户端进程中创建的代理的 CLSID 的指针。  
  
 *pCid*  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK否则为 S_FALSE。  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)