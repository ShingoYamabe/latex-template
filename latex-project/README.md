# Docker 使ってLaTeXをコンパイルする環境を整えよう！



## 準備編



### VS Code 上で LaTeX コンパイルを可能にする．

* docker-compose.yamlがある場所で下記を実行して、イメージをビルドしてコンテナを立ち上げます。

``` 
docker compose up -d
docker compose ps
```
または
``` 
docker-compose up -d
docker-compose ps
```

コンテナの立ち上がりを確認したら VS Code からアタッチします．

左下の><みたいなのからWSL : Ubuntu のボタンを押すとドロップダウンが出るので，

"実行中のコンテナにアタッチする"を選択してアタッチ．

\*\*コンテナ内で\*\*　VSCode拡張のLatex Workshopをインストールして有効に

⚙ > 設定 > 📄JSONで開く > 下記を追加．

```json

"latex-workshop.latex.tools": \[

&#x20;   {

&#x20;     "name": "latexmk-uplatex",

&#x20;     "command": "latexmk",

&#x20;     "args": \[

&#x20;       "-e","$latex=uplatex",

&#x20;       "-e","$bibtex=biber",

&#x20;       "-e","$dvipdf='dvipdfmx %O -o %D %S'",

&#x20;       "-e","$pdf\_mode=3",              // uplatex → dvipdfmx でPDF化

&#x20;       "-synctex=1",

&#x20;       "-interaction=nonstopmode",

&#x20;       "-file-line-error",

&#x20;       "%DOC%"

&#x20;     ]

&#x20;   }

&#x20; ],

&#x20; "latex-workshop.latex.recipes": \[

&#x20;   { "name": "uplatex -> dvipdfmx", "tools": \["latexmk-uplatex"] }

&#x20; ],

&#x20; "latex-workshop.latex.recipe.default": "uplatex -> dvipdfmx"

```





\## texファイルを作成してコンパイル(三角のやつ)を押すとdviとpdfが出てくるはず

