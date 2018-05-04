---
title: 引用计数 (ATL) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- AddRef method [C++], reference counting
- reference counting
- AddRef method [C++]
- reference counts
- references, counting
ms.assetid: b1fd4514-6de6-429f-9e60-2777c0d07a3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1ba27f00bf25f88575101b1299daf50f94000ad
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="reference-counting"></a>引用计数
COM 本身不会自动尝试从内存中移除一个对象，当它认为不再使用对象。 相反，该对象的程序员必须删除未使用的对象。 程序员确定是否可以移除一个对象基于引用计数。  
  
 COM 使用**IUnknown**方法， [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379)和[版本](http://msdn.microsoft.com/library/windows/desktop/ms682317)，以便管理对某个对象的接口引用计数。 调用这些方法的一般规则是：  
  
-   每当客户端接收的接口指针，`AddRef`必须在接口上调用。  
  
-   每当客户端已完成使用的接口指针，则必须调用**版本**。  
  
 在简单实现中，每个`AddRef`调用递增和每个**版本**调用在对象内的计数器变量的递减。 当计数返回为零时，接口不再有任何用户，并且可以随时将其自身从内存中移除。  
  
 引用计数还可以实现以便计数 （不与单个接口） 的对象对每个引用。 在这种情况下，每个`AddRef`和**版本**对对象调用委托给中央实现和**版本**时引用计数变为零时释放整个对象。  
  
> [!NOTE]
>  当`CComObject`-派生的对象使用构造**新**运算符，引用计数为 0。 因此，调用`AddRef`必须在成功创建后进行`CComObject`-派生对象。  
  
## <a name="see-also"></a>请参阅  
 [COM 简介](../atl/introduction-to-com.md)   
 [管理通过引用计数对象生存期](http://msdn.microsoft.com/library/windows/desktop/ms687260)

