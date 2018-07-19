---
title: 'Ftmbase:: Getunmarshalclass 方法 |Microsoft 文档'
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
ms.openlocfilehash: 09afd9f977dbc779eb1dc10e9553d2ca88538fcc
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873298"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass 方法
获取 COM 用来定位 DLL 包含代码的相应的代理的 CLSID。 COM 加载此 DLL 才能创建代理服务器的未初始化的实例。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
#### <a name="parameters"></a>参数  
 `riid`  
 对要封送的接口标识符的引用。  
  
 `pv`  
 指向要封送处理; 接口如果调用方不具有到所需的接口指针，则可以为 NULL。  
  
 `dwDestContext`  
 其中将是取消封送指定的接口的目标上下文。  
  
 指定一个或多个 MSHCTX 枚举值。  
  
 在当前进程 (MSHCTX_INPROC) 的另一单元，或在当前进程 (MSHCTX_LOCAL) 所在的计算机上的另一个进程中，会发生取消封送。  
  
 `pvDestContext`  
 留待将来使用;必须为 NULL。  
  
 `mshlflags`  
 此操作完成后，指向要用于在客户端进程中创建代理的 CLSID。  
  
 `pCid`  
  
## <a name="return-value"></a>返回值  
 如果成功，则则为 S_OK否则为 S_FALSE。  
  
## <a name="requirements"></a>要求  
 **标头：** ftm.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [FtmBase 类](../windows/ftmbase-class.md)