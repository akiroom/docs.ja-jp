---
title: ICorDebugInternalFrame2::IsCloserToLeaf メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0e72d15ab4ca9b4468efb2a671022f30bfb3cc6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759947"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf メソッド
チェックするかどうか、`this`内部フレームは、指定した ICorDebugFrame オブジェクトよりも、リーフに近いです。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pFrameToCompare`  
 [in]比較へのポインター`ICorDebugFrame`オブジェクト。  
  
 `pIsCloser`  
 [out]`true`場合、`this`内部フレームがで指定されたフレームよりも近いリーフのため`pFrameToCompare`、それ以外の`false`します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|比較が正常に実行されました。|  
|E_FAIL|比較を実行できませんでした。|  
|E_INVALIDARG|`pFrameToCompare` または `pIsCloser` が null です。|  
  
## <a name="remarks"></a>Remarks  
 `IsCloserToLeaf` スタック上の他のフレームを持つ内部フレームをインターリーブのポリシーを実装するために使用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugInternalFrame2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
