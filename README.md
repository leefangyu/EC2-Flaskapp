# 簡介
部署一個Flask App到AWS EC2 Instance上
使外部能透過public ip連線到該雲端server訪問Flask App

# 建立AWS EC2 Instance
登入帳號後至EC2 啟動新執行個體
可選擇使用哪種OS
![](https://hackmd.io/_uploads/SkoWAGtga.png)

建立金鑰對可以讓外部透過SSH連線到此instance
![](https://hackmd.io/_uploads/ByazCzKgT.png)

建立安全群組來允許browser存取server
![](https://hackmd.io/_uploads/rkQNRfKxT.png)

Instance建立完成
![](https://hackmd.io/_uploads/ByFdAMteT.png)

有提供多種選項連線至Instance
此例使用EC2 Instance Connect連線
![](https://hackmd.io/_uploads/BkrLJXFga.png)

# 安裝相關軟體及套件
```shell=
#更新apt庫
sudo apt update 
#安裝python
sudo apt install python3
#安裝pip
sudo apt install python3-pip
#安裝git
sudo apt install git-all
#安裝 flask
sudo apt install python3-flask
```

# 開始部署
clone flask app下來
```shell
git clone https://github.com/leefangyu/EC2-Flaskapp.git
```

到安全群組新增傳入規則
![](https://hackmd.io/_uploads/Hy3ZFXYla.png)

新增port5000讓外部能透過port5000存取server
![](https://hackmd.io/_uploads/B1HUtQFla.png)

執行flask app
```shell
flask run --host=0.0.0.0
```

host參數可指定Flask App綁定的 IP 位址
預設為 127.0.0.1，表示只能從本機訪問該應用程式
如果將 host 設置為 0.0.0.0
表示該應用程式將會綁定到本機的所有網路介面
即可從本機任何 IP 位址訪問該應用程式

**執行結果**
可從外部透過public ip加上設定的port連到server
完成部署
![](https://hackmd.io/_uploads/H1azsmKlp.png)


# Reference
https://blog.csdn.net/FriendshipTang/article/details/110870647

https://cosinechen.medium.com/aws-ec2-%E4%B8%8A%E4%BD%BF%E7%94%A8-nginx-lets-encrypt-%E9%83%A8%E7%BD%B2-flask-%E6%87%89%E7%94%A8%E7%A8%8B%E5%BC%8F-8c04c0f44a6d