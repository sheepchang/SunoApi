<div align="center">

[简体中文](README_ZH.md) | [Русский язык](README_RU.md) | [English](README.md) | [한국어](README_KR.md) | [日本語](README_JP.md)


![GitHub last commit](https://img.shields.io/github/last-commit/SunoApi/SunoApi) | ![GitHub commit activity](https://img.shields.io/github/commit-activity/t/SunoApi/SunoApi) | ![GitHub Issues or Pull Requests](https://img.shields.io/github/issues/SunoApi/SunoApi) | ![SunoApi GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/SunoApi/SunoApi/total)


# 祝賀本開源項目入選本周weekly
### [![ruanyf](https://avatars.githubusercontent.com/u/905434?s=20) ruanyf added the weekly label 12 hours ago](https://github.com/ruanyf/weekly/issues/4263)

</div>


# Suno API 非官方 Suno AI 用戶端

- 這是一個基於Python、Streamlit的非官方Suno API用戶端，現時支持生成音樂，獲取音樂資訊等功能。自帶維護token與保活功能，無需擔心token過期問題，可以設定多個帳號的資訊保存以便使用。

- GitHub有時候訪問不到，如無法訪問請移步Gitee地址： https://gitee.com/SunoApi/SunoApi

### 特點

- Token自動維護與保活
- 可以設定多個帳號的資訊保存使用
- 程式碼簡單，易於維護，方便二次開發

### 調試

#### Python本地調試運行

- 安裝依賴

```bash
pip3 install -r requirements.txt
```

- 啟動項目，關於Streamlit請自行參攷Streamlit檔案

```bash
streamlit run main.py
```

### 部署

#### Docker 本地一鍵部署

```bash
docker run -d \
  --name sunoapi \
  --restart always \
  -p 8501:8501 \
  sunoapi/sunoapi:latest
```

#### Docker 本地編譯部署

```bash
docker compose build && docker compose up
```

#### Dockerfile

```docker
FROM python:3.10-slim-buster

WORKDIR /app

COPY requirements.txt ./
RUN --mount=type=cache,target=/root/.cache/pip \
    pip install -r requirements.txt --no-cache-dir

COPY . .

EXPOSE 8501
CMD [ "nohup", "streamlit", "run", "main.py" ]
```

#### Docker 拉取鏡像部署

```bash
docker-compose pull && docker-compose up -d
```

#### docker-compose.yml

```docker
version: '3.1'

services:
  sunoapi:
    image: sunoapi/sunoapi:latest
    container_name: sunoapi
    ports:
      - "8501:8501"
    volumes:
      - ./sunoapi.db:/app/sunoapi.db
    restart: always
```

#### Streamlit 遠程倉庫部署

- 先Fork一份SunoApi程式碼到你的Github倉庫裡面
- 選擇Github授權登入： https://share.streamlit.io/
- 打開部署頁面： https://share.streamlit.io/deploy
- Repository選擇：SunoApi/SunoApi
- Branch輸入：main
- Main file path輸入：main.py
- 點擊Deploy！

#### Zeabur 一鍵部署

[![Deploy on Zeabur](https://zeabur.com/button.svg)](https://zeabur.com/templates/5BLAEZ)

### 配寘

- 先從瀏覽器頁面登入狀態下中獲取自己的session和cookie。

![session](https://sunoapi.net/images/session.png)

- 填寫設定資訊裡面後面會自動保活，可以填寫多個帳號資訊。

![session1](https://sunoapi.net/images/session1.png)

- 填寫後保存資訊，輸入identity可以更改修改帳號資訊。

![session2](https://sunoapi.net/images/session2.png)

### 完成

- 啟動運行項目後瀏覽器訪問 http://localhost:8501/ 即可使用了。

![index1](https://sunoapi.net/images/index1.png)

![index](https://sunoapi.net/images/index.png)


### 問題

- 如果頁面一直提示：請先設定資訊保存，然後再刷新頁面才能正常使用！ 請先添加自己的帳號資訊保存，然後把sunoapi.db資料庫裡面其他無效的帳號資訊删除，其中包括我測試的帳號資訊，然後再就可以正常使用了。
- 音樂生成任務提交成功後拉取生成任務隊列狀態，當狀態為“complete”時成功返回，這個時候默認停留了15秒等待官方生成檔案。 官方介面服務直接返回了媒體檔案Url地址，大部分時候頁面能正常顯示這些媒體檔案。 偶爾有時候介面已經返回了媒體檔案Url地址，但是實際檔案還不能從Url地址訪問到要等一會。 這個時候媒體檔案在頁面就可能無法加載到，可以點下媒體播放機滑鼠右鍵複製媒體檔案地址，用瀏覽器單獨打開這個地址就可以訪問到了或者直接右鍵另存為下載保存。
- 關於設定帳號session和cookie資訊保存安全性問題，只要你的帳號不充值就沒必要擔心，因為不知道你的帳號密碼，你填寫的session和cookie資訊只要你的帳號在其他地方登入活動，或者在官方網站退出登入，那麼填寫的session和cookie就無效了，並且下次登入官網session和cookie都會發生變化的。


### 創作

- 專業歌詞輔助工具： https://poe.com/SuperSunoMaster


### 交流

- Github Issues： https://github.com/SunoApi/SunoApi/issues

<img src="https://sunoapi.net/images/wechat.jpg" width="382px" height="511px" />


### 參與

- 個人的力量始終有限，任何形式的貢獻都是歡迎的，包括但不限於貢獻程式碼，優化檔案，提交Issue和PR，由於時間有限不接受在微信或者微信群給開發者提Bug，有問題或者優化建議請提交Issue和PR！

[![Star History Chart](https://api.star-history.com/svg?repos=SunoApi/SunoApi&type=Timeline)](https://star-history.com/#SunoApi/SunoApi&Timeline)


### 參攷

- Suno AI 官網: [https://suno.com](https://suno.com)
- Suno-API: [https://github.com/SunoAI-API/Suno-API](https://github.com/SunoAI-API/Suno-API)


### 聲明

- SunoApi是一個非官方的開源項目，僅供學習和研究使用。用戶自願輸入免費的帳號資訊生成音樂。 每個帳戶每天可以免費生成五首歌曲，我們不會將它們用於其他目的。請放心使用！如果有10000名用戶，那麼系統每天可以免費生成50000首歌曲。請儘量節省使用量，因為每個帳戶每天只能免費生成五首歌曲。如果每個人每天創作五首以上的歌曲，這仍然不够。 最終目標是讓在需要的時候能隨時免費生成。
