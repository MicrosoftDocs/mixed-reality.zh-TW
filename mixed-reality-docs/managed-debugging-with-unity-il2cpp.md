---
title: 使用 Unity IL2CPP 的 Managed 調試
description: 本文涵蓋如何在 Unity IL2CPP UWP 專案上執行 managed 偵錯工具。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: unity，visual studio，調試，il2cpp
ms.openlocfilehash: 970d3000df995e7c6e331a41d10e25dc5aa370a8
ms.sourcegitcommit: 7e8b9de561cbc8483e84511f3e9cbd779f3a999f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/27/2019
ms.locfileid: "75502659"
---
# <a name="managed-debugging-with-unity-il2cpp"></a>使用 Unity IL2CPP 的 Managed 調試

請遵循下列步驟，將 managed 偵錯工具附加至您的 Unity IL2CPP UWP 組建。 本指南最初是針對 HoloLens 和 HoloLens 2 而開發。

1. 您必須位於支援[多播](https://en.wikipedia.org/wiki/Multicast)的網路上。
1. 請確定**InternetClientServer**和**PrivateNetworkClientServer**在 UWP 發行設定功能下已簽入 Unity。

    ![UWP 發行設定功能](images/il2cpp-debugging-capabilities.png)

1. 設定 Unity UWP 組建設定：
    - 開發組建
    - 指令碼偵錯
    - 等候受管理的偵錯工具（選擇性）

    ![UWP 組建設定](images/il2cpp-debugging-build.png)

1. Unity 中的組建。
1. 建立 Visual Studio 解決方案，並將其部署到您的裝置。 您應該使用**Debug**或**Release**設定來建立。 **主要**設定會停用 Unity profiler，並防止優化的調試。 （選擇性）在解決方案的 package.appxmanifest.xml 中，確認 [功能] 清單中的 [**網際網路（用戶端 & 伺服器）** ] 和 [**私人網路（用戶端 & 伺服器）** ]。
1. 在您的裝置上啟動應用程式。 請確定您的裝置已連線到與您電腦相同的網路。
1. 請確定裝置**未**透過 USB 連接到您的電腦。
1. 當您按兩下 Unity 中的腳本時所建立的 Visual Studio 方案，您可以在其中查看及編輯C#腳本。
1. Debug-> 附加 Unity 偵錯工具。

    ![附加 Unity 偵錯工具](images/il2cpp-debugging-attach.png)

1. 在清單中選取您的裝置，然後按一下 [確定] 以連接。

    ![裝置清單](images/il2cpp-debugging-machines.png)
