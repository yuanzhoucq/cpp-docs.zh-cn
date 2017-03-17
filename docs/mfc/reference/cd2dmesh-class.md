---
title: "CD2DMesh 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CD2DMesh
- AFXRENDERTARGET/CD2DMesh
- AFXRENDERTARGET/CD2DMesh::CD2DMesh
- AFXRENDERTARGET/CD2DMesh::Attach
- AFXRENDERTARGET/CD2DMesh::Create
- AFXRENDERTARGET/CD2DMesh::Destroy
- AFXRENDERTARGET/CD2DMesh::Detach
- AFXRENDERTARGET/CD2DMesh::Get
- AFXRENDERTARGET/CD2DMesh::IsValid
- AFXRENDERTARGET/CD2DMesh::Open
- AFXRENDERTARGET/CD2DMesh::m_pMesh
dev_langs:
- C++
helpviewer_keywords:
- CD2DMesh class
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 78461adeaa0671b146ccb48f4e9145cbdceeb8cf
ms.lasthandoff: 02/24/2017

---
# <a name="cd2dmesh-class"></a>CD2DMesh 类
ID2D1Mesh 包装器。  
  
## <a name="syntax"></a>语法  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DMesh::CD2DMesh](#cd2dmesh)|构造 CD2DMesh 对象。|  
|[CD2DMesh:: ~ CD2DMesh](#_dtorcd2dmesh)|析构函数。 当 D2D 网格对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DMesh::Attach](#attach)|附加现有的资源的对象的接口|  
|[CD2DMesh::Create](#create)|创建 CD2DMesh。 (重写[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create)。)|  
|[CD2DMesh::Destroy](#destroy)|销毁 CD2DMesh 对象。 (重写[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy)。)|  
|[CD2DMesh::Detach](#detach)|分离对象中的资源接口|  
|[CD2DMesh::Get](#get)|返回 ID2D1Mesh 接口|  
|[CD2DMesh::IsValid](#isvalid)|检查资源的有效性 (重写[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid)。)|  
|[CD2DMesh::Open](#open)|此时将打开用于填充的网格。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CD2DMesh::operator ID2D1Mesh *](#operator_id2d1mesh_star)|返回 ID2D1Mesh 接口|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CD2DMesh::m_pMesh](#m_pmesh)|指向 ID2D1Mesh 的指针。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 `CD2DMesh`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxrendertarget.h  
  
##  <a name="_dtorcd2dmesh"></a>CD2DMesh:: ~ CD2DMesh  
 析构函数。 当 D2D 网格对象被销毁时调用。  
  
```  
virtual ~CD2DMesh();
```  
  
##  <a name="attach"></a>CD2DMesh::Attach  
 附加现有的资源的对象的接口  
  
```  
void Attach(ID2D1Mesh* pResource);
```  
  
### <a name="parameters"></a>参数  
 `pResource`  
 现有资源的接口。 不能为 NULL  
  
##  <a name="cd2dmesh"></a>CD2DMesh::CD2DMesh  
 构造 CD2DMesh 对象。  
  
```  
CD2DMesh(
    CRenderTarget* pParentTarget,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pParentTarget`  
 指向该呈现器目标的指针。  
  
 `bAutoDestroy`  
 指示所有者 (pParentTarget) 将销毁该对象。  
  
##  <a name="create"></a>CD2DMesh::Create  
 创建 CD2DMesh。  
  
```  
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```  
  
### <a name="parameters"></a>参数  
 `pRenderTarget`  
 指向该呈现器目标的指针。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="destroy"></a>CD2DMesh::Destroy  
 销毁 CD2DMesh 对象。  
  
```  
virtual void Destroy();
```  
  
##  <a name="detach"></a>CD2DMesh::Detach  
 分离对象中的资源接口  
  
```  
ID2D1Mesh* Detach();
```  
  
### <a name="return-value"></a>返回值  
 指向已分离的资源接口指针。  
  
##  <a name="get"></a>CD2DMesh::Get  
 返回 ID2D1Mesh 接口  
  
```  
ID2D1Mesh* Get();
```  
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Mesh 接口或者如果对象尚未初始化为 NULL 指针。  
  
##  <a name="isvalid"></a>CD2DMesh::IsValid  
 检查资源的有效性  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果资源是有效，则为，TRUE否则为 FALSE。  
  
##  <a name="m_pmesh"></a>CD2DMesh::m_pMesh  
 指向 ID2D1Mesh 的指针。  
  
```  
ID2D1Mesh* m_pMesh;  
```  
  
##  <a name="open"></a>CD2DMesh::Open  
 此时将打开用于填充的网格。  
  
```  
ID2D1TessellationSink* Open();
```  
  
### <a name="return-value"></a>返回值  
 用于填充网格 ID2D1TessellationSink 指向的指针。  
  
##  <a name="operator_id2d1mesh_star"></a>CD2DMesh::operator ID2D1Mesh *  
 返回 ID2D1Mesh 接口  
  
```  
operator ID2D1Mesh*();
```   
  
### <a name="return-value"></a>返回值  
 指向 ID2D1Mesh 接口或者如果对象尚未初始化为 NULL 指针。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

