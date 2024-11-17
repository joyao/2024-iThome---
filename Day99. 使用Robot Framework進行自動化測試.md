
## Robot Framework的介紹

是一個開源免費的自動化框架，可以用於自動化測試和依照流程進行自動化執行。

請使用Python3.11或以下的版本，Python3.12還有很多相容性的問題
### 安裝robot framework python package
``` bash
python -m pip install robotframework
python -m pip install setuptools
python -m pip install rpaframework
```

### 安裝VS Code robot framework extension

安裝
- Robocorp Code
- Robot Framework Language Server

![[Pasted image 20240911225859.png]]

### 建立script

ctrl + p 輸入
```
> Robocorp: Create Task Package
> Robocorp: Robot Framework - Browser automation with Playwright
```

開啟tasks.robot






---
新增一個檔案 tests.robot

``` robot
*** Test Cases ***
First Test Case
    Log    Hello world
```

執行
![[Pasted image 20240911225155.png]]