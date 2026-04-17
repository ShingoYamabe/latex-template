# texliveの公式イメージを使う
FROM texlive/texlive:latest

# Dockerfile の後半（USER texlive の前など）に追加
USER root
RUN mkdir -p /home/texlive/.vscode-server/bin /home/texlive/.vscode-server/data \
    && chown -R texlive:texlive /home/texlive/.vscode-server

USER texlive

# 初期ディレクトリの設定
WORKDIR /home/$USERNAME/src