# 安裝docker
Docker 安裝檔 [https://docs.docker.com/docker-for-windows/install/](https://docs.docker.com/docker-for-windows/install/)

Docker 在Windows需要透過VM技術運行，視乎情況，可能需要"WSL 2"或者"HyperV"。

其中HyperV可以經過Enable Windows Feature來取得，可能會容易安裝一點。

如果安裝HyperV時出現Error，很可能你的主機板BIOS的VM功能還未打開，一般Intel 64bit CPU的主機都可以在BIOS中找到。但這個比較難以做教學，需要自行在BIOS中找一找。

# Docker 設定
Docker 在安裝過程中應該會問你想用哪一種container，我們要選Linux container

Docker 安裝完後可以設定虛擬CPU和RAM的數量，以我經驗，跑Server最少要2G RAM。CPU看情況，1個虛擬CPU也可以。

# Nginx RTMP Server
在github 下載相關程式設定檔。github右上角可以你會見到 Code => Download Zip

Zip檔請解壓縮在一個比較單純的Windows路徑下，例如C:\\\\nginxRtmp或D:\\\\nginxRtmp

Windows路徑行中最好不要有空格，就是不要放在"Program Files"等的資料夾內。

解壓後，在你解壓縮的資料夾下，打開Windows Power Shell（應該Windows Explorer可以直接打開[看圖](https://www.howtogeek.com/wp-content/uploads/2020/03/2020-03-16_17h12_38.png?trim=1,1&bg-color=000&pad=1,1)），(請使用有管理員權限的Windows Power Shell)

然後，打上指令
```
docker-compose up -d
```
因為版本差異，有時可能要打 
```
docker-compose.exe up -d
```

想要結束時，打指令
```
docker-compose down
```
或
```
docker-compose.exe down
```

## 串流上載
成開跑起docker-compose後，使用obs可以進行上傳

server: rtmp://伺服器IP:1935/live

stream key: 隨便你

若Server在家中，server就是可以用
```
rtmp://127.0.0.1:1935/live
```
stream key 隨便給一個
```
test1
```

## 串流下載
如果上載成功的話，可以使用VLC或者OBS，讀取剛剛的位置，但格式會變成
```
rtmp://127.0.0.1:1935/live/test1
```