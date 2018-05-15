## 安裝 VirtualBox

依照您的作業系統類型，安裝 5.x 以上最新版本的 VirtualBox 軟體，建議同時安裝「VirtualBox Extension Pack」以支援虛擬機器的進階功能。

* VirtualBox 下載頁面 https://www.virtualbox.org/wiki/Downloads
* 安裝 VirtualBox Extension Pack 之步驟可以參考[這份文件](http://www.arthurtoday.com/2011/01/oracle-vm-virtualbox-40-extension-pack_14.html)。

![下載必要的 VirtualBox 安裝檔案](download-virtualbox.png)

### vt-x amd-v 異常造成 VM 無法開啟

在執行 VM 時出現下列訊行

> 電腦問題(0022) - VirtualBox 錯誤訊息 VT-x/AMD-V 硬體加速在您的系統不可用

我們可以透過下面步驟來進行排除

#### BIOS 設定

##### Intel

在 Intel 電腦的 BIOS 中，(有可能是在 Advanced，或者 CPU Configuration 裡面) 找一個名稱如 Intel Virtual Technology 或 Virtualization 之類的選項，如果原設定是 Disabled，則將它改為 Enabled 之後再儲存，離開 BIOS 重開機就可以了。

##### AMD

在 AMD 電腦的 BIOS 中，(有可能是在 Advanced，或者 CPU/System Configuration 裡面) 找一個名稱是 SVM Mode 或 Virtualization Technology 或 Virtualization 之類的去改為 Enabled，儲存之後離開 BIOS，再重開機就可以了。

## 參考資料

<https://notepad-of-steven.blogspot.tw/2015/08/0022-virtualbox-vt-xamd-v.html>