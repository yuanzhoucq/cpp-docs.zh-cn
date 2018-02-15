---
title: CDBPropSet::AddProperty | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
dev_langs:
- C++
helpviewer_keywords:
- AddProperty method
ms.assetid: dc9539d3-1ee4-40f3-9281-2068e6d65e93
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d71e3e2b86c631cc2e9d0a3516c46cb418737d7b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="cdbpropsetaddproperty"></a>CDBPropSet::AddProperty
将属性添加到属性集。  
  
## <a name="syntax"></a>语法  
  
```
bool AddProperty(DWORD dwPropertyID,   
   constVARIANT& var,   
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,  
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,  
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();  
```  
  
#### <a name="parameters"></a>参数  
 *dwPropertyID*  
 [in]要添加的属性 ID。 用于初始化**dwPropertyID**的`DBPROP`添加到属性集的结构。  
  
 `var`  
 [in]用于初始化的属性值的一个变体`DBPROP`添加到属性集的结构。  
  
 `szValue`  
 [in]用于初始化的属性值的字符串`DBPROP`添加到属性集的结构。  
  
 `bValue`  
 [in]A**字节**或布尔值用于初始化的属性值`DBPROP`添加到属性集的结构。  
  
 `nValue`  
 [in]用于初始化的属性值的整数值`DBPROP`添加到属性集的结构。  
  
 *fltValue*  
 [in]用于初始化的属性值的浮点值`DBPROP`添加到属性集的结构。  
  
 `dblValue`  
 [in]用于初始化的属性值的双精度浮点值`DBPROP`添加到属性集的结构。  
  
 `cyValue`  
 [in]用于初始化的属性值的 CY 货币值`DBPROP`添加到属性集的结构。  
  
## <a name="return-value"></a>返回值  
 **true**如果已成功添加属性。 否则为**false**。  
  
## <a name="requirements"></a>惠?  
 **标头:** atldbcli.h  
  
## <a name="see-also"></a>请参阅  
 [CDBPropSet 类](../../data/oledb/cdbpropset-class.md)   
 [需要的 DBPROP 结构](https://msdn.microsoft.com/en-us/library/ms717970.aspx)